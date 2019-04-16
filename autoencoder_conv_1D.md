def create_model(inp_shape, out_shape):
    afun = 'relu'
    bfun = 'tanh'
    pad = 'same'

    n_filters = 10

    # upsample the prediction result in the end
    final_upsampling = 1
    dense_layer_out_size = np.int(np.prod(out_shape) / (n_filters * final_upsampling))
    n_pooling = 4

    model = Sequential()
    #model.add(MaxPooling1D())
    model.add(Conv1D(filters=4, kernel_size=7, activation=afun, padding=pad, input_shape=inp_shape))
    #     model.add(BatchNormalization())
    model.add(MaxPooling1D())

    model.add(Conv1D(filters=8, kernel_size=7, activation=afun, padding=pad))
    #     model.add(BatchNormalization())
    model.add(MaxPooling1D())

    model.add(Conv1D(filters=16, kernel_size=7, activation=afun, padding=pad))
    #     model.add(BatchNormalization())
    model.add(MaxPooling1D(3))


    model.add(Conv1D(filters=n_filters, kernel_size=11, activation=afun, padding=pad))
    #     model.add(BatchNormalization())
    model.add(MaxPooling1D(n_pooling))

    model.add(Flatten())
    model.add(Dense(dense_layer_out_size, activation='tanh'))
    model.add(Reshape((dense_layer_out_size, 1)))
    model.add(Conv1D(filters=4*n_filters, kernel_size=11, activation=bfun, padding=pad))
    model.add(Conv1D(filters=2*n_filters, kernel_size=3, activation=bfun, padding=pad))
    model.add(Conv1D(filters=n_filters, kernel_size=7, activation=bfun, padding=pad))
    model.add(Conv1D(filters=n_filters, kernel_size=7, activation='linear', padding=pad))
    #model.add(MaxPooling1D())
    model.add(UpSampling1D(size=final_upsampling))
    #model.add(Flatten())

    ########  Comment

    #model.add(Dropout(0.25))
    #model.add(Dense(np.prod(out_shape), activation='linear'));
    ########
    #     model.add(Dropout(0.5))
    model.add(Reshape(out_shape))

    return model