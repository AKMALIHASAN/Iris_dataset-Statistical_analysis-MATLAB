# Iris_dataset-Statistical_analysis-MATLAB
Statistical analysis on Iris dataset by MATLAB

At first we need to load the dataset to MATLAB. We will use the text version of the dataset. The dataset has 4 non-class attributes- Sepal Length, Sepal Width, Petal Length, Petal Width and a class attribute of Species.
While loading we will split it into few parts. At first we will load the 4 non-class attributes as a separate dataset. As they are in txt format and separate by comma so the command will be following---


% attrib1--sepal length in cm
% attrib2--sepal width in cm
% attrib3--petal length in cm
% attrib4--petal width in cm

[attrib1, attrib2, attrib3, attrib4, class] = textread('iris_data.txt', '%f%f%f%f%s', 'delimiter', ',');

Now we will also combine the 4 non-class attributes in one dataset

attrib = [attrib1'; attrib2'; attrib3'; attrib4']';
We can calculate the mean for each attributes separately or together. As the attrib dataset contains all the 4 non class attributes value together. 
>> mean(attrib)
ans =
5.8433              3.0540         3.7587              1.1987                           mean values in cm

Sepal length        Sepal width    Petal length        Petal width                      non-class attributes



Median of the 4 non class attributes 

>> median (attrib)
ans =
    5.8000                 3.0000               4.3500                1.3000                     median values in cm                                                                               
   Sepal length            Sepal width          Petal length          Petal width                non-class attributes


Standard Deviation of the 4 non class attributes 

>> std(attrib)
ans =
    0.8281                  0.4336            1.7644                  0.7632                                  Standard deviation in cm                                                                                           
   Sepal length             Sepal width        Petal length           Petal width                             non-class attributes




Min of the 4 non class attributes 

>> min (attrib)
ans =
    4.3000                  2.0000            1.0000                  0.1000                                 minimum values 
   Sepal length            Sepal width        Petal length            Petal width                            non-class attributes

Max of the 4 non class attributes 

>> max (attrib)
ans =
    7.9000                  4.4000             6.9000                   2.5000                               maximum values 
   Sepal length             Sepal width        Petal length             Petal width                          non-class attributes

Now we will level our class attributes species. As they are string and they have 3 different types species, we can divide and define them into 1,2,3.

label = zeros(150, 1);
label(strcmp(class, 'Iris-setosa')) = 1;
label(strcmp(class, 'Iris-versicolor')) = 2;
label(strcmp(class, 'Iris-virginica')) = 3;



As we defined 1 as Iris-setosa, 2 as Iris-versicolor and 3 as Iris-virginica, so can get the frequency table from our label dataset by using tabulate function--

>> tabulate(label)

  Value    Count   Percent
      1       50     33.33%
      2       50     33.33%
      3       50     33.33%
	one-dimensional histogram of petal length attribute
>> hist(attrib3)
	Scatter plot of attributes of petal length and petal width
Now we will plot the scatter for petal width and petal length and for better view of the graph we used legend for different symbol and colors to represent the species- setosa as x, versicolor as + and virginica as o,  and to append and keep the subsequent plot we used hold function
Pt_length_width = [attrib3,attrib4];
index1 = find(label == 1);
index2 = find(label == 2);
index3 = find(label == 3);
Pt_length_width1 = Pt_length_width(index1,:);
Pt_length_width2 = Pt_length_width(index2,:);
Pt_length_width3 = Pt_length_width(index3,:);
 
plot(Pt_length_width1(:,1), Pt_length_width1(:,2), 'bx');
hold on;
plot(Pt_length_width2(:,1), Pt_length_width2(:,2), 'g+');
hold on;
plot(Pt_length_width3(:,1), Pt_length_width3(:,2), 'ro');
 
hl = legend('setosa','versicolor','virginica');
set(hl,'Orientation','vertical');
 
xlabel('Petal Length');
ylabel('Petal Width');
