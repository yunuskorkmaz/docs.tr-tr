---
title: Varlık etkinlikleri
ms.date: 03/30/2017
ms.assetid: c04f7413-7fb8-40c6-819e-dc92b145b62e
ms.openlocfilehash: 96301c15b849749299e744a435068c3ec9be2e3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="entity-activities"></a>Varlık etkinlikleri
Bu örnek ADO.NET Entity Framework ile Windows Workflow Foundation veri erişimi basitleştirmek için nasıl kullanılacağını gösterir.  
  
 ADO.NET Entity Framework, özellikler ve ilişkiler müşteriler, siparişler, sipariş ayrıntılarını ve bu varlıkları arasındaki ilişkileri gibi etki alanına özgü nesneleri biçiminde verilerle çalışmak geliştiricilerin sağlar. ADO.NET Entity Framework bunu doğrudan bir ilişkisel depolama şema karşı programlama yerine kavramsal uygulama modeli karşı programlama etkinleştirir özet düzeyi sağlayarak gerçekleştirir. ADO.NET Entity Framework bakın hakkında daha fazla bilgi için [ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549).  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnekte `Northwind` veritabanı ve oluşturma ve kaldırma için komutlar içerir `Northwind` veritabanı (Setup.cmd ve Cleanup.cmd). Bu örnek projelerinde göre bir varlık veri modeli dahil `Northwind` veritabanı. Model açarak bulabileceğiniz `Northwind.edmx` projeye dahil dosyası. ADO.NET Entity Framework kullanılarak erişilebilir nesnelerin şeklini tanımlayan modeli budur.  
  
 Bu örnekte aşağıdaki etkinlikleri bulunmaktadır:  
  
-   `EntitySQLQuery``EntitySQLQuery` Etkinliği bir varlık SQL sorgu dizesine dayalı veritabanından nesneleri almanıza olanak sağlar. Varlık SQL, SQL için benzer bir mağaza bağımsız dildir ve kavramsal model ve model veya etki alanının parçası olan varlıkların temel alan sorgular belirtmenize olanak tanır. Varlık SQL dili ile ilgili daha fazla bilgi için bkz: [varlık SQL dil](http://go.microsoft.com/fwlink/?LinkId=165646).  
  
-   `EntityLinqQuery`: Bu etkinlik, bir LINQ Sorgu veya koşulu göre veritabanından nesneleri almanıza olanak tanır.  
  
-   `EntityAdd``EntityAdd` Etkinlik, bir varlık veya bir varlıklar koleksiyonu veritabanına eklemenize olanak sağlar.  
  
-   `EntityDelete``EntityDelete` Etkinlik, bir varlık veya bir varlıklar koleksiyonu veritabanından silmek sağlar.  
  
-   `ObjectContextScope`: Yukarıda açıklanan etkinlikler içeren bir içinde yalnızca kullanılabilir `ObjectContextScope` etkinliği örneği. `ObjectContextScope` Etkinlik veritabanına bağlantı kurar. (Ya da geçirilen veya bir yapılandırma dosyası ayarı kullanılarak alınıp) bir bağlantı dizesi gerektirir. `ObjectContextScope` Etkinlik grubu varlıkları ilgili işlemlerinin gerçekleştirmek kolaylaştırır. Bu kapsam etkin bir bağlantı korur, Hayır kalıcı bir kapsam demektir. Ayrıca, `ObjectContextScope` etkinlik çıkar, varlık etkinlikleri kullanarak bu kapsamı içinde otomatik olarak alınan nesnelere yapılan değişiklikleri veritabanına kalıcı ve nesneleri geri için hiçbir açık veya sonraki bir eylem gerekli Veritabanı.  
  
## <a name="using-the-entity-activities"></a>Varlık etkinlikleri kullanma  
 Aşağıdaki kod parçacıkları, bu örnekte sunulan varlık etkinlikleri kullanımını göstermektedir.  
  
### <a name="entitysql"></a>EntitySql  
 Aşağıdaki kod parçacığında adına göre sıralanmış Londra'daki tüm müşteriler sorgulama ve müşterilerin listesini yineleme gösterir.  
  
```  
Variable<IEnumerable<Customer>> londonCustomers = new Variable<IEnumerable<Customer>>();  
DelegateInArgument<Customer> iterationVariable = new DelegateInArgument<Customer>();  
  
// create and return the workflow  
return new ObjectContextScope  
{  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Variables = { londonCustomers },  
    Body = new Sequence  
        {  
            Activities =   
                {               
                    new WriteLine { Text = "Executing query" },                            
                    // query for all customers that are in london   
                    new EntitySqlQuery<Customer>  
                    {  
                        EntitySql =  @"SELECT VALUE Customer   
                                        FROM NorthwindEntities.Customers AS Customer   
                                        WHERE Customer.City = 'London'   
                                        ORDER BY Customer.ContactName",  
                        Result = londonCustomers  
                    },  
  
                    // iterate through the list of customers and display them   
                    new ForEach<Customer>  
                    {                                      
                        Values = londonCustomers,  
                        Body = new ActivityAction<Customer>  
                        {  
                            Argument = iterationVariable,  
                            Handler = new WriteLine   
                            {   
                                  Text = new InArgument<String>(e =>    
                                              iterationVariable.Get(e).ContactName)   
                            }  
                        }  
                    }  
                }  
        }                 
};     
```  
  
### <a name="entitylinqquery"></a>EntityLinqQuery  
 Aşağıdaki kod parçacığında, Londra'daki tüm müşteriler sorgulama ve ortaya çıkan müşteriler listesi yineleme gösterir.  
  
```  
Variable<IEnumerable<Customer>> londonCustomers = new Variable<IEnumerable<Customer>>() { Name = "LondonCustomers" };  
DelegateInArgument<Customer> iterationVariable = new DelegateInArgument<Customer>() { Name = "iterationVariable" };  
  
return new ObjectContextScope  
{  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Variables = { londonCustomers },  
    Body = new Sequence  
    {  
        Activities =   
        {               
            // return all the customers that match with the provided Linq predicate  
            new EntityLinqQuery<Customer>  
            {   
                Predicate = new LambdaValue<Func<Customer, bool>>(  
                          ctx => new Func<Customer, bool>(c => c.City.Equals("London"))),                              
                Result = londonCustomers  
            },  
  
            // iterate through the list of customers and display in the console  
            new ForEach<Customer>  
            {                                      
                Values = londonCustomers,  
                Body = new ActivityAction<Customer>  
                {  
                    Argument = iterationVariable,  
                    Handler = new WriteLine   
                    {   
                        Text = new InArgument<String>(e =>   
                                      iterationVariable.Get(e).ContactName)   
                    }  
                }  
            }  
        }  
    }  
};  
```  
  
### <a name="entityadd"></a>EntityAdd  
 Aşağıdaki kod parçacığında, bir OrderDetail kaydı için var olan bir siparişi ekleme gösterilmektedir.  
  
```  
Variable<IEnumerable<Order>> orders = new Variable<IEnumerable<Order>>();  
Variable<IEnumerable<OrderDetail>> orderDetails = new Variable<IEnumerable<OrderDetail>>();  
Variable<Order> order = new Variable<Order>();  
Variable<OrderDetail> orderDetail = new Variable<OrderDetail>();              
  
return new ObjectContextScope  
{  
    Variables = { order, orders, orderDetail, orderDetails },  
    ContainerName = "NorthwindEntities",  
    ConnectionString = new InArgument<string>(connStr),                  
    Body = new Sequence  
    {                      
        Activities =   
        {                            
           // get the order where we want to add the detail  
           new EntitySqlQuery<Order>  
           {  
               EntitySql =    
                    @"SELECT VALUE [Order]  
                      FROM NorthwindEntities.Orders as [Order]  
                      WHERE Order.OrderID == 10249",  
               Result = orders  
           },  
  
           // store the order in a variable  
           new Assign<Order>   
           {  
               To = new OutArgument<Order>(order),  
               Value = new InArgument<Order>(c => orders.Get(c).First<Order>())  
           },  
  
           // add the detail to the order  
           new EntityAdd<OrderDetail>  
           {  
               Entity = new InArgument<OrderDetail>(c =>   
                                         new OrderDetail {   
                                                  OrderID=10249, ProductID=11,   
                                                  Quantity=1, UnitPrice = 15,   
                                                  Discount = 0, Order = order.Get(c) })  
           }  
        }  
    }  
};  
```  
  
### <a name="entitydelete"></a>EntityDelete  
 Aşağıdaki kod parçacığında, (varsa) bir sırada varolan OrderDetail kaydını silmek gösterilmiştir.  
  
```  
Variable<IEnumerable<OrderDetail>> orderDetails = new Variable<IEnumerable<OrderDetail>>();              
  
return new ObjectContextScope  
{  
    Variables = { orderDetails },  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Body = new Sequence  
    {  
        Activities =   
        {               
            // find the entitiy to be deleted (order detail for product 11 in order 10249)  
            new EntitySqlQuery<OrderDetail>  
            {  
                EntitySql = @"SELECT VALUE OrderDetail  
                                FROM NorthwindEntities.OrderDetails as OrderDetail  
                               WHERE OrderDetail.OrderID == 10249   
                                 AND OrderDetail.ProductID == 11",  
                Result = orderDetails  
            },  
  
            // if the order detail is found, delete it, otherwise, display a message  
            new If  
            {  
                Condition = new InArgument<bool>(c=>orderDetails.Get(c).Count() > 0),  
                Then = new Sequence  
                {   
                    Activities =   
                    {                                      
                        new EntityDelete<OrderDetail>  
                        {  
                            Entity = new InArgument<OrderDetail>(c =>   
                                              orderDetails.Get(c).First<OrderDetail>())  
                        },  
                    }  
                },                              
                Else = new WriteLine { Text = "Order Detail for Deleting not found" }                              
            }                                                  
        }  
    }  
};  
```  
  
## <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
 Oluşturmanız gerekir `Northwind` Bu örneği çalıştırmadan önce yerel SQL server Express örneği veritabanında.  
  
#### <a name="to-set-up-the-northwind-database"></a>Northwind veritabanı ayarlamak için  
  
1.  Bir komut istemi açın.  
  
2.  Yeni bir komut istemi penceresinde EntityActivities\CS klasöre gidin.  
  
3.  Tür `setup.cmd` ve ENTER tuşuna basın.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], EntityActivities.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
 Bu örnek çalıştırdıktan sonra kaldırmak isteyebilirsiniz `Northwind` veritabanı.  
  
#### <a name="to-uninstall-the-northwind-database"></a>Northwind veritabanı kaldırmak için  
  
1.  Bir komut istemi açın.  
  
2.  Yeni bir komut istemi penceresinde EntityActivities\CS klasöre gidin.  
  
3.  Tür `cleanup.cmd` ve ENTER tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`