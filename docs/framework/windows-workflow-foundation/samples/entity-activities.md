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
# <a name="entity-activities"></a><span data-ttu-id="14c41-102">Varlık etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="14c41-102">Entity Activities</span></span>
<span data-ttu-id="14c41-103">Bu örnek, ADO.NET Entity Framework ile Windows Workflow Foundation veri erişimini basitleştirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="14c41-103">This sample shows how to use the ADO.NET Entity Framework with Windows Workflow Foundation to simplify data access.</span></span>  
  
 <span data-ttu-id="14c41-104">ADO.NET varlık çerçevesi, geliştiricilerin etki alanına özgü nesneler, özellikler ve ilişkiler gibi müşteri, sipariş, sipariş ayrıntılarını ve bu varlıkları arasındaki ilişkileri biçiminde verilerle çalışmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="14c41-104">The ADO.NET Entity Framework enables developers to work with data in the form of domain-specific objects, properties and relationships such as Customers, Orders, Order Details and the relationships between these entities.</span></span> <span data-ttu-id="14c41-105">ADO.NET varlık çerçevesi yerine doğrudan bir ilişkisel depolama şemaya karşı programlama bir uygulama kavramsal modeline karşı programlama sağlar soyutlama düzeyini sağlayarak bunu yapar.</span><span class="sxs-lookup"><span data-stu-id="14c41-105">The ADO.NET Entity Framework does this by providing a level of abstraction that enables programming against a conceptual application model instead of programming directly against a relational storage schema.</span></span> <span data-ttu-id="14c41-106">ADO.NET Entity Framework bakın hakkında daha fazla bilgi için [ADO.NET Entity Framework](https://go.microsoft.com/fwlink/?LinkId=165549).</span><span class="sxs-lookup"><span data-stu-id="14c41-106">For more information about the ADO.NET Entity Framework see [ADO.NET Entity Framework](https://go.microsoft.com/fwlink/?LinkId=165549).</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="14c41-107">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="14c41-107">Sample details</span></span>  
 <span data-ttu-id="14c41-108">Bu örnekte `Northwind` oluşturma ve kaldırma betiklerini içerir ve veritabanı `Northwind` veritabanı (Setup.cmd ve Cleanup.cmd).</span><span class="sxs-lookup"><span data-stu-id="14c41-108">This sample uses the `Northwind` database and includes scripts for creating and removing the `Northwind` database (Setup.cmd and Cleanup.cmd).</span></span> <span data-ttu-id="14c41-109">Projeleri bu temel bir varlık veri modeli içeren `Northwind` veritabanı.</span><span class="sxs-lookup"><span data-stu-id="14c41-109">The projects in this sample include an Entity Data Model based on the `Northwind` database.</span></span> <span data-ttu-id="14c41-110">Model açarak bulabilirsiniz `Northwind.edmx` projeye dahil dosya.</span><span class="sxs-lookup"><span data-stu-id="14c41-110">You can find the model by opening the `Northwind.edmx` file that is included in the project.</span></span> <span data-ttu-id="14c41-111">Bu, ADO.NET varlık çerçevesi kullanılarak erişilebilir nesneleri şeklini tanımlayan modelidir.</span><span class="sxs-lookup"><span data-stu-id="14c41-111">This is the model that defines the shape of the objects that can be accessed using the ADO.NET Entity Framework.</span></span>  
  
 <span data-ttu-id="14c41-112">Bu örnekte aşağıdaki etkinlikleri dahildir:</span><span class="sxs-lookup"><span data-stu-id="14c41-112">The following activities are included in this sample:</span></span>  
  
-   <span data-ttu-id="14c41-113">`EntitySQLQuery``EntitySQLQuery` Etkinliği veritabanından bir varlık SQL sorgu dizesine göre nesneleri almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="14c41-113">`EntitySQLQuery`: The `EntitySQLQuery` activity allows you to retrieve objects from the database based on an Entity SQL query string.</span></span> <span data-ttu-id="14c41-114">Entity SQL SQL'e benzeyen bir depo bağımsız dilidir ve kavramsal model ve model veya etki alanının parçası olan varlıklar üzerinde temel alan sorguları belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="14c41-114">Entity SQL is a store independent language that is similar to SQL and it allows you to specify queries based on the conceptual model and the entities that are a part of the model or domain.</span></span> <span data-ttu-id="14c41-115">Entity SQL dili hakkında daha fazla bilgi için bkz: [Entity SQL dili](https://go.microsoft.com/fwlink/?LinkId=165646).</span><span class="sxs-lookup"><span data-stu-id="14c41-115">For more information about Entity SQL Language, see [Entity SQL Language](https://go.microsoft.com/fwlink/?LinkId=165646).</span></span>  
  
-   <span data-ttu-id="14c41-116">`EntityLinqQuery`: Bu etkinlik bir LINQ Sorgu veya koşulu temel veritabanından nesneleri almanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="14c41-116">`EntityLinqQuery`: This activity allows you to retrieve objects from the database based on a LINQ query or predicate.</span></span>  
  
-   <span data-ttu-id="14c41-117">`EntityAdd``EntityAdd` Etkinlik, bir varlığı veya varlık koleksiyonunu veritabanına eklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="14c41-117">`EntityAdd`: The `EntityAdd` activity allows you to add an entity or a collection of entities to the database.</span></span>  
  
-   <span data-ttu-id="14c41-118">`EntityDelete``EntityDelete` Etkinlik veritabanından bir varlık veya varlık koleksiyonunu silmek olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="14c41-118">`EntityDelete`: The `EntityDelete` activity allows you to delete an entity or a collection of entities from the database.</span></span>  
  
-   <span data-ttu-id="14c41-119">`ObjectContextScope`: Daha önce bahsedilen etkinlikleri içeren içinde yalnızca kullanılabilir `ObjectContextScope` etkinlik örneği.</span><span class="sxs-lookup"><span data-stu-id="14c41-119">`ObjectContextScope`: The previously mentioned activities can only be used within a containing `ObjectContextScope` activity instance.</span></span> <span data-ttu-id="14c41-120">`ObjectContextScope` Etkinlik veritabanına bir bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="14c41-120">The `ObjectContextScope` activity sets up the connection to the database.</span></span> <span data-ttu-id="14c41-121">(Ya da geçirilen veya bir yapılandırma dosyası ayarı kullanarak) bir bağlantı dizesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="14c41-121">It requires a connection string (that is either passed in or retrieved using a configuration file setting).</span></span> <span data-ttu-id="14c41-122">`ObjectContextScope` Etkinlik bir grup varlıklardaki ilgili işlemler gerçekleştirmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="14c41-122">The `ObjectContextScope` activity makes it easy to perform a group of related operations on entities.</span></span> <span data-ttu-id="14c41-123">Bu kapsam etkin bir bağlantı tutar, Hayır kalıcı bir kapsam olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="14c41-123">Because this scope maintains an active connection, it is a No Persist scope.</span></span> <span data-ttu-id="14c41-124">Buna ek olarak, `ObjectContextScope` etkinlik çıkar, varlık etkinliklerini kullanarak bu kapsam içinde otomatik olarak alınan nesnelere yapılan değişiklikleri veritabanına geri kalıcı ve hiçbir açık veya sonraki eylem nesnelerini yedeklemek için gereklidir Veritabanı.</span><span class="sxs-lookup"><span data-stu-id="14c41-124">In addition, when the `ObjectContextScope` activity exits, any changes that are made to objects retrieved using Entity Activities within that scope automatically get persisted back to the database, and no explicit or subsequent action is required to save objects back to the database.</span></span>  
  
## <a name="using-the-entity-activities"></a><span data-ttu-id="14c41-125">Varlık etkinlikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="14c41-125">Using the entity activities</span></span>  
 <span data-ttu-id="14c41-126">Aşağıdaki kod parçacıkları, bu örnekte sunulan varlık etkinlikleri kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="14c41-126">The following code snippets demonstrate how to use the entity activities presented in this sample.</span></span>  
  
### <a name="entitysql"></a><span data-ttu-id="14c41-127">EntitySql</span><span class="sxs-lookup"><span data-stu-id="14c41-127">EntitySql</span></span>  
 <span data-ttu-id="14c41-128">Aşağıdaki kod parçacığında, Londra'daki adına göre sıralanmış tüm müşterilerin sorgulama ve müşterilerin listesi boyunca yineleme yapmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="14c41-128">The code snippet below shows how to query all customers in London sorted by name and how to iterate through the list of customers.</span></span>  
  
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
  
### <a name="entitylinqquery"></a><span data-ttu-id="14c41-129">EntityLinqQuery</span><span class="sxs-lookup"><span data-stu-id="14c41-129">EntityLinqQuery</span></span>  
 <span data-ttu-id="14c41-130">Aşağıdaki kod parçacığında, Londra'daki tüm müşteriler sorgulama ve müşteriler sonuç listesi boyunca yineleme yapmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="14c41-130">The code snippet below shows how to query all customers in London and how to iterate through the resulting list of customers.</span></span>  
  
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
  
### <a name="entityadd"></a><span data-ttu-id="14c41-131">EntityAdd</span><span class="sxs-lookup"><span data-stu-id="14c41-131">EntityAdd</span></span>  
 <span data-ttu-id="14c41-132">Aşağıdaki kod parçacığında, bir OrderDetail kaydı var olan bir siparişi ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="14c41-132">The code snippet below shows how to add an OrderDetail record to an existing Order.</span></span>  
  
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
  
### <a name="entitydelete"></a><span data-ttu-id="14c41-133">EntityDelete</span><span class="sxs-lookup"><span data-stu-id="14c41-133">EntityDelete</span></span>  
 <span data-ttu-id="14c41-134">Aşağıdaki kod parçacığında, (varsa) bir sırada varolan OrderDetail kaydını Sil işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="14c41-134">The code snippet below shows how to delete an existing OrderDetail record in an Order (if it exists).</span></span>  
  
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
  
## <a name="to-use-this-sample"></a><span data-ttu-id="14c41-135">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="14c41-135">To use this sample</span></span>  
 <span data-ttu-id="14c41-136">Oluşturmalısınız `Northwind` veritabanında bu örneği çalıştırmadan önce yerel SQL server Express örneği.</span><span class="sxs-lookup"><span data-stu-id="14c41-136">You must create the `Northwind` database in your local SQL server Express instance before running this sample.</span></span>  
  
#### <a name="to-set-up-the-northwind-database"></a><span data-ttu-id="14c41-137">Northwind veritabanı ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="14c41-137">To set up the Northwind database</span></span>  
  
1.  <span data-ttu-id="14c41-138">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="14c41-138">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="14c41-139">Yeni komut istemi penceresinde EntityActivities\CS klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="14c41-139">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="14c41-140">Tür `setup.cmd` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="14c41-140">Type `setup.cmd` and press ENTER.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="14c41-141">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="14c41-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="14c41-142">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], EntityActivities.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="14c41-142">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EntityActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="14c41-143">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="14c41-143">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="14c41-144">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="14c41-144">To run the solution, press CTRL+F5.</span></span>  
  
 <span data-ttu-id="14c41-145">Bu örnek çalıştırdıktan sonra kaldırmak isteyebilirsiniz `Northwind` veritabanı.</span><span class="sxs-lookup"><span data-stu-id="14c41-145">After running this sample, you may want to remove the `Northwind` database.</span></span>  
  
#### <a name="to-uninstall-the-northwind-database"></a><span data-ttu-id="14c41-146">Northwind veritabanı kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="14c41-146">To uninstall the Northwind database</span></span>  
  
1.  <span data-ttu-id="14c41-147">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="14c41-147">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="14c41-148">Yeni komut istemi penceresinde EntityActivities\CS klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="14c41-148">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="14c41-149">Tür `cleanup.cmd` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="14c41-149">Type `cleanup.cmd` and press ENTER.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="14c41-150">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="14c41-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="14c41-151">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="14c41-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="14c41-152">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="14c41-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="14c41-153">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="14c41-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`