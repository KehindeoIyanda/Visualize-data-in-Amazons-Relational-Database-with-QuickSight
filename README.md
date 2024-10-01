# Visualize-data-in-Amazons-Relational-Database-with-QuickSight
![](Assets/Visualize%20a%20Relational%20Database.drawio.png)

## Create a Relational Database
- Create a relational database from scratch


  ![](Assets/-001.png)
  ![](Assets/-002.png)
## Connect RDS to MySQL Workbench
  Now that we've got our relational database shell in AWS, we need to create a few tables and enter in some data.
  To do this we'll be using one of the most popular database tools in the world, MySQL Workbench from Oracle.
  
  - Make your RDS instance public, to allow connections from outside the AWS network (ie. from our local machine using MySQL Workbench)
  - Download MySQL Workbench
  - Modify the security group attached to your RDS instance so that your local machine can access your RDS instance.
  - Connect MySQL Workbench to your RDS.

    
     ![](Assets/-003.png)
     ![](Assets/-004.png)
     ![](Assets/-005.png)
     ![](Assets/-006.png)

## Create Database Tables and Load Data
Now that we've got our MySQL Workbench connected with our RDS instance, we can actually start to add our own tables and data.
 - Create a new schema using MySQL Workbench
 - Create two new tables in your schema
 - Populate those tables with data using SQL


   ![](Assets/-007.png)
   ![](Assets/-008.png)
   ![](Assets/-009.png)
   ![](Assets/-010.png)
   

## Connect RDS to QuickSight
- Adjust the security group attached to our RDS instance to allow inbound requests from QuickSight.
- Add your RDS instance as a data source in QuickSight.


 ![](Assets/-011.png)
 ![](Assets/-014.png)

## Secure QuickSight

- Create a new security group for QuickSight
- Attach QuickSight to our new security group


  ![](Assets/-015.png)
  ![](Assets/-016.png)

- Update role the IAM Role by Clicking into the aws-quicksight-service-role-v0
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeVpcs",
        "ec2:DescribeSubnets",
        "ec2:DescribeSecurityGroups",
        "ec2:DescribeNetworkInterfaces",
        "ec2:CreateNetworkInterface",
        "ec2:DeleteNetworkInterface",
        "ec2:ModifyNetworkInterfaceAttribute",
        "iam:PassRole"
      ],
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "iam:PassRole"
      ],
      "Resource": "*"
    }
  ]
}
```

![](Assets/-018.png)

## Secure RDS 

- Make our RDS instance private instead of publicly accessible.
- Create a new security group specially for our RDS instance.
- Give our QuickSight security group access to our RDS securtiy group so they can talk to each other.


![](Assets/-019.png)
![](Assets/-020.png)
![](Assets/-021.png)
![](Assets/-022.png)
![](Assets/-023.png)

## Reconnect RDS with QuickSight

- Create a dataset in QuickSight to connect with our new security group
- Choose the table we want to query to create our charts

![](Assets/-024.png)
![](Assets/-025.png)
![](Assets/-026.png)

## Make some charts

![](Assets/-027.png)
![](Assets/-028.png)
