# kpi
CREATE TABLE Driver
(
ID_Driver INT primary key,
First_Name VARCHAR(50),
Last_Name VARCHAR(50),
Efficiency FLOAT
);
ALTER TABLE Driver ADD PRIMARY KEY (ID_Driver);

CREATE TABLE Transport
(ID_Transport INT NOT NULL,
ID_Vehicle INT NOT NULL,
ID_Driver INT NOT NULL,
State_Vehicle VARCHAR(50)
);
ALTER TABLE Transport ADD PRIMARY KEY (ID_Transport);


CREATE TABLE Product
(ID_Product INT NOT NULL,
Name_Product VARCHAR(50) NOT NULL,
Volume FLOAT NOT NULL,
Mass FLOAT NOT NULL,
Price FLOAT NOT NULL
);
ALTER TABLE Product ADD PRIMARY KEY (ID_Product);

CREATE TABLE Vehicle
(ID_Vehicle INT NOT NULL,
Name_Vehicle VARCHAR(50),
Max_Capacity FLOAT NOT NULL,
Max_Mass FLOAT NOT NULL
);
ALTER TABLE Vehicle ADD PRIMARY KEY (ID_Vehicle);

CREATE TABLE Client
(ID_Client INT NOT NULL,
Name_Client VARCHAR(100) NOT NULL,
Location VARCHAR(150) NOT NULL
);
ALTER TABLE Client ADD PRIMARY KEY (ID_Client);

CREATE TABLE Cargo
(ID_Cargo INT NOT NULL,
ID_Command INT NOT NULL
);
ALTER TABLE Cargo ADD PRIMARY KEY (ID_Cargo);

CREATE TABLE Command
(ID_Command INT primary key NOT NULL,
ID_Client INT NOT NULL,
ID_Product INT NOT NULL,
Time_Order DATE NOT NULL,
Time_Delivery DATE,
Quantity INT NOT NULL,
Total_Mass FLOAT,
Total_Volume FLOAT,
ID_Cargo INT NOT NULL
);

alter table Command add constraint fk1 foreign key (ID_Client) references Client(ID_Client);
alter table Command add constraint fk2 foreign key (ID_Product) references Product(ID_Product);
alter table Command add constraint fk3 foreign key (ID_Cargo) references Cargo(ID_Cargo);

alter table Transport add constraint fk4 foreign key (ID_Vehicle) references Vehicle(ID_Vehicle);
alter table Transport add constraint fk5 foreign key (ID_Driver) references Driver(ID_Driver);

alter table Cargo add constraint fk6 foreign key(ID_Command) references Command(ID_Command);
