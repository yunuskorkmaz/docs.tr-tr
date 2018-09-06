---
title: Varlık etkinlikleri
ms.date: 03/30/2017
ms.assetid: c04f7413-7fb8-40c6-819e-dc92b145b62e
ms.openlocfilehash: 03bd0e42c70f1226558d492bcb3b2cfa5c7010f2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861159"
---
# <a name="entity-activities"></a>Varlık etkinlikleri
Bu örnek, ADO.NET Entity Framework ile Windows Workflow Foundation veri erişimini basitleştirmek için nasıl kullanılacağını gösterir.  
  
 ADO.NET varlık çerçevesi, geliştiricilerin etki alanına özgü nesneler, özellikler ve ilişkiler gibi müşteri, sipariş, sipariş ayrıntılarını ve bu varlıkları arasındaki ilişkileri biçiminde verilerle çalışmanıza olanak tanır. ADO.NET varlık çerçevesi yerine doğrudan bir ilişkisel depolama şemaya karşı programlama bir uygulama kavramsal modeline karşı programlama sağlar soyutlama düzeyini sağlayarak bunu yapar. ADO.NET Entity Framework bakın hakkında daha fazla bilgi için [ADO.NET Entity Framework](https://go.microsoft.com/fwlink/?LinkId=165549).  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnekte `Northwind` oluşturma ve kaldırma betiklerini içerir ve veritabanı `Northwind` veritabanı (Setup.cmd ve Cleanup.cmd). Projeleri bu temel bir varlık veri modeli içeren `Northwind` veritabanı. Model açarak bulabilirsiniz `Northwind.edmx` projeye dahil dosya. Bu, ADO.NET varlık çerçevesi kullanılarak erişilebilir nesneleri şeklini tanımlayan modelidir.  
  
 Bu örnekte aşağıdaki etkinlikleri dahildir:  
  
-   `EntitySQLQuery``EntitySQLQuery` Etkinliği veritabanından bir varlık SQL sorgu dizesine göre nesneleri almanızı sağlar. Entity SQL SQL'e benzeyen bir depo bağımsız dilidir ve kavramsal model ve model veya etki alanının parçası olan varlıklar üzerinde temel alan sorguları belirtmenize olanak sağlar. Entity SQL dili hakkında daha fazla bilgi için bkz: [Entity SQL dili](https://go.microsoft.com/fwlink/?LinkId=165646).  
  
-   `EntityLinqQuery`: Bu etkinlik bir LINQ Sorgu veya koşulu temel veritabanından nesneleri almanıza olanak tanır.  
  
-   `EntityAdd``EntityAdd` Etkinlik, bir varlığı veya varlık koleksiyonunu veritabanına eklemenize olanak sağlar.  
  
-   `EntityDelete``EntityDelete` Etkinlik veritabanından bir varlık veya varlık koleksiyonunu silmek olanak tanır.  
  
-   `ObjectContextScope`: Daha önce bahsedilen etkinlikleri içeren içinde yalnızca kullanılabilir `ObjectContextScope` etkinlik örneği. `ObjectContextScope` Etkinlik veritabanına bir bağlantı kurar. (Ya da geçirilen veya bir yapılandırma dosyası ayarı kullanarak) bir bağlantı dizesi gerekir. `ObjectContextScope` Etkinlik bir grup varlıklardaki ilgili işlemler gerçekleştirmesini kolaylaştırır. Bu kapsam etkin bir bağlantı tutar, Hayır kalıcı bir kapsam olmasıdır. Buna ek olarak, `ObjectContextScope` etkinlik çıkar, varlık etkinliklerini kullanarak bu kapsam içinde otomatik olarak alınan nesnelere yapılan değişiklikleri veritabanına geri kalıcı ve hiçbir açık veya sonraki eylem nesnelerini yedeklemek için gereklidir Veritabanı.  
  
## <a name="using-the-entity-activities"></a>Varlık etkinlikleri kullanma  
 Aşağıdaki kod parçacıkları, bu örnekte sunulan varlık etkinlikleri kullanımını göstermektedir.  
  
### <a name="entitysql"></a>EntitySql  
 Aşağıdaki kod parçacığında, Londra'daki adına göre sıralanmış tüm müşterilerin sorgulama ve müşterilerin listesi boyunca yineleme yapmak nasıl gösterir.  
  
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
 Aşağıdaki kod parçacığında, Londra'daki tüm müşteriler sorgulama ve müşteriler sonuç listesi boyunca yineleme yapmak nasıl gösterir.  
  
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
 Aşağıdaki kod parçacığında, bir OrderDetail kaydı var olan bir siparişi ekleme işlemi gösterilmektedir.  
  
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
 Aşağıdaki kod parçacığında, (varsa) bir sırada varolan OrderDetail kaydını Sil işlemi gösterilmektedir.  
  
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
 Oluşturmalısınız `Northwind` veritabanında bu örneği çalıştırmadan önce yerel SQL server Express örneği.  
  
#### <a name="to-set-up-the-northwind-database"></a>Northwind veritabanı ayarlamak için  
  
1.  Bir komut istemi açın.  
  
2.  Yeni komut istemi penceresinde EntityActivities\CS klasöre gidin.  
  
3.  Tür `setup.cmd` ve ENTER tuşuna basın.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], EntityActivities.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
 Bu örnek çalıştırdıktan sonra kaldırmak isteyebilirsiniz `Northwind` veritabanı.  
  
#### <a name="to-uninstall-the-northwind-database"></a>Northwind veritabanı kaldırmak için  
  
1.  Bir komut istemi açın.  
  
2.  Yeni komut istemi penceresinde EntityActivities\CS klasöre gidin.  
  
3.  Tür `cleanup.cmd` ve ENTER tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`