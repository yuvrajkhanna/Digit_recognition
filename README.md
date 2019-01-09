# Digit Recognition
**Digit recognition using keras model:<br/>
training custom made model on MNIST dataset using keras<br/>
**


**EXPLANATION**<br/>
import required libraries
![](images/digit_1.PNG)

load our csv file
![](images/digit_2.PNG)

select label column in dataframe train as our Y_train which will be our labels.<br/>
Drop that label column and seect everything else which will be out pixel values of each image.<br/>
now to check if data is symmetrically distributed among all our labels that is 0-9<br/>
we check it by printing them and there plot using **seaborn** library which we imported as sns
![](images/digit_3.PNG)

to preprocess the data normalise it by divinding it with 255 as 255 is max value a single pixel can have.<br/>
see shape of single image is 1,784(28x28) as it is known,input to **Convolutional layer** is an image.<br/>
reshape it to 28x28 so we can use **conv layer** as our 1st layer.<br/>
our Y_train is numeric form. convert it to vector form by using **to_categorical.**<br/>
eg. 3 --> (0,0,0,1,0,0,0,0,0,0)
![](images/digit_4.PNG)

split date into 2 parts to use 2nd part for validation I have used 0.9-0.1 split in out case.<br/>
we do this to make sure our model is not **overfitting**.<br/>
![](images/digit_5.PNG)

created a simple model.<br/>
here in 1st line when we add **conv2D layer** --><br/>
we have to mension imput_size of each image in our 1st layer of our model.(28x28x1)<br/>
our image is gray scaled so its **depth is 1** that is why there is 28x28x1 image not 28x28.<br/>
if it was coloured it is usually represented with RGB that is of **depth 3**.<br/>
**filters** mean depth of our layer after convolution.<br/>
**kernel_size** is filter size that convolve over our image.<br/>
**padding** is 0s we put to have image of size we want after convolution.<br/>
it is good to use activation after every conv layer so we use **relu activation** as it is very less coputationally expensive.<br/>
this ends our **convolutional layer**.<br/>
**max pool layer** simpy chooses maximum from its filter nothing to explain.<br/>
**dropout layer** is used to avoid overfitting.<br/>
**flatten** converts the tensor like output from conv layers to a vector which can be used in **dense(simple neural net)** layer.<br/>
our last layer have only 10 units as our output is a vecotor of (1x10).<br/>
since it is last layer we can use better activation that is softmax
![](images/digit_6.PNG)

once our model is ready we compile it by choosing a **optimizer,loss function** if necessary choose a **learning rate reduction** method as well<br/>
![](images/digit_7.PNG)

we can create more data by **data augementation** method which simpy changes images little bit<br/>
solving our problem of having less data. :) <br/>
![](images/digit_8.PNG)

train the model(by the way verbose means how you want to show your training process)<br/>
![](images/digit_9.PNG)

predict the test case<br/>
remember output would be 1x10 vector for each image convert it into 1x1 choosing index of max value among them<br/>
save it in dataframe and create csv file.<br/>
![](images/digit_10.PNG)

please share if this helped :)
