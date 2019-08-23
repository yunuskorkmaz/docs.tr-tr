---
title: N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: ccd30e3d1b0d716b6393fdb093d47cddf7302f8d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963269"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="ecea5-102">N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="ecea5-102">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>
<span data-ttu-id="ecea5-103">Müşteriler veya siparişler gibi varlık nesnelerini bir ağ üzerinden bir istemciye serileştirçalıştığınızda, bu varlıklar veri bağlamlarından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="ecea5-103">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="ecea5-104">Veri bağlamı artık yaptıkları değişiklikleri veya ilişkilerini diğer nesnelerle izlemediğinden.</span><span class="sxs-lookup"><span data-stu-id="ecea5-104">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="ecea5-105">Bu, istemcilerin yalnızca verileri okuduğu sürece bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-105">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="ecea5-106">Ayrıca, istemcilerin bir veritabanına yeni satırlar eklemesini sağlamak oldukça kolaydır.</span><span class="sxs-lookup"><span data-stu-id="ecea5-106">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="ecea5-107">Bununla birlikte, uygulamanız, istemcilerin verileri güncelleştirebilmesini veya silmesine gerek duymalıdır, çağrı <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>yapmadan önce varlıkları yeni bir veri bağlamına iliştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-107">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ecea5-108">Buna ek olarak, özgün değerlerle iyimser eşzamanlılık denetimi kullanıyorsanız, veritabanını hem özgün varlık hem de varlığı değiştirilmiş olarak sağlamak için bir yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-108">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="ecea5-109">Yöntemler `Attach` , daha sonra varlıkları kullanımdan kaldırıldıktan sonra yeni bir veri bağlamına yerleştirmeye olanak tanımak için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-109">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="ecea5-110">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Varlıkların yerine ara sunucu nesnelerini serileştirseniz bile, verileri veritabanına göndermek için veri erişim katmanında (dal) bir varlık oluşturmanız ve bunu yeni <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>bir ile bağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-110">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="ecea5-111">varlıkların serileştirilme şekli hakkında tamamen farklıdır.</span><span class="sxs-lookup"><span data-stu-id="ecea5-111">is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="ecea5-112">Windows Communication Foundation (WCF) kullanılarak seri hale getirilebilir sınıflar oluşturmak için nesne ilişkisel Tasarımcısı ve SQLMetal araçlarının nasıl kullanılacağı hakkında daha fazla bilgi için bkz [. nasıl yapılır: Varlıkları seri hale](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)getirilebilir yapın.</span><span class="sxs-lookup"><span data-stu-id="ecea5-112">For more information about how to use the Object Relational Designer and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ecea5-113">Yalnızca yeni veya `Attach` Serisi kaldırılan varlıklarda Yöntemleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="ecea5-113">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="ecea5-114">Bir varlığın özgün veri bağlamından ayrılması için tek yol, onun serileştirilmesi içindir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-114">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="ecea5-115">Ayrılmamış bir varlığı yeni bir veri bağlamına iliştirmeye çalışırsanız ve bu varlığın önceki veri bağlamından [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ertelenmiş yükleyiciler varsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ecea5-115">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="ecea5-116">İki farklı veri bağlamlarından ertelenmiş yükleyicileriyle bir varlık, bu varlıkta ekleme, güncelleştirme ve silme işlemlerini gerçekleştirdiğinizde istenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-116">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="ecea5-117">Ertelenmiş yükleyiciler hakkında daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="ecea5-117">For more information about deferred loaders, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="ecea5-118">Veri alma</span><span class="sxs-lookup"><span data-stu-id="ecea5-118">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="ecea5-119">İstemci yöntemi çağrısı</span><span class="sxs-lookup"><span data-stu-id="ecea5-119">Client Method Call</span></span>  
 <span data-ttu-id="ecea5-120">Aşağıdaki örneklerde, bir Windows Forms istemcisinden DAL için örnek yöntem çağrısı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-120">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="ecea5-121">Bu örnekte, DAL bir Windows hizmet kitaplığı olarak uygulanır:</span><span class="sxs-lookup"><span data-stu-id="ecea5-121">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
```vb  
Private Function GetProdsByCat_Click(ByVal sender As Object, ByVal e _  
    As EventArgs)  
  
    ' Create the WCF client proxy.  
    Dim proxy As New NorthwindServiceReference.Service1Client  
  
    ' Call the method on the service.  
    Dim products As NorthwindServiceReference.Product() = _  
        proxy.GetProductsByCategory(1)  
  
    ' If the database uses original values for concurrency checks,  
    ' the client needs to store them and pass them back to the  
    ' middle tier along with the new values when updating data.  
  
    For Each v As NorthwindClient1.NorthwindServiceReference.Product _  
        In products  
        ' Persist to a List(Of Product) declared at class scope.  
        ' Additional change-tracking logic is the responsibility  
        ' of the presentation tier and/or middle tier.  
        originalProducts.Add(v)  
    Next  
  
    ' (Not shown) Bind the products list to a control  
    ' and/or perform whatever processing is necessary.  
End Function  
```  
  
```csharp  
private void GetProdsByCat_Click(object sender, EventArgs e)  
{  
    // Create the WCF client proxy.  
    NorthwindServiceReference.Service1Client proxy =   
    new NorthwindClient.NorthwindServiceReference.Service1Client();  
  
    // Call the method on the service.  
    NorthwindServiceReference.Product[] products =   
    proxy.GetProductsByCategory(1);  
  
    // If the database uses original values for concurrency checks,   
    // the client needs to store them and pass them back to the   
    // middle tier along with the new values when updating data.  
    foreach (var v in products)  
    {  
        // Persist to a list<Product> declared at class scope.  
        // Additional change-tracking logic is the responsibility  
        // of the presentation tier and/or middle tier.  
        originalProducts.Add(v);  
    }  
  
    // (Not shown) Bind the products list to a control  
    // and/or perform whatever processing is necessary.  
    }  
```  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="ecea5-122">Orta katman uygulama</span><span class="sxs-lookup"><span data-stu-id="ecea5-122">Middle Tier Implementation</span></span>  
 <span data-ttu-id="ecea5-123">Aşağıdaki örnek, Orta katmanda arabirim yönteminin bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-123">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="ecea5-124">Aşağıda, aklınızda iki ana işaret verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ecea5-124">The following are the two main points to note:</span></span>  
  
- <span data-ttu-id="ecea5-125">, <xref:System.Data.Linq.DataContext> Yöntem kapsamında bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-125">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
- <span data-ttu-id="ecea5-126">Yöntemi, gerçek sonuçların <xref:System.Collections.IEnumerable> bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ecea5-126">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="ecea5-127">Seri hale getirici, sonuçları istemci/sunum katmanına geri göndermek için sorguyu yürütür.</span><span class="sxs-lookup"><span data-stu-id="ecea5-127">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="ecea5-128">Sorgu sonuçlarına yerel olarak Orta katmanda erişmek için, sorgu değişkenine veya `ToList` `ToArray` öğesini çağırarak yürütmeye zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecea5-128">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="ecea5-129">Daha sonra, bu listeyi veya diziyi bir `IEnumerable`olarak döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecea5-129">You can then return that list or array as an `IEnumerable`.</span></span>  
  
```vb  
Public Function GetProductsByCategory(ByVal categoryID As Integer) _  
    As IEnumerable(Of Product)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    Dim productQuery = _  
    From prod In db.Products _  
    Where prod.CategoryID = categoryID _  
    Select prod  
  
    Return productQuery.AsEnumerable()  
  
End Function  
```  
  
```csharp  
public IEnumerable<Product> GetProductsByCategory(int categoryID)  
{  
    NorthwindClasses1DataContext db =   
    new NorthwindClasses1DataContext(connectionString);  
  
    IEnumerable<Product> productQuery =  
    from prod in db.Products  
    where prod.CategoryID == categoryID  
    select prod;  
  
    return productQuery.AsEnumerable();   
}  
```  
  
 <span data-ttu-id="ecea5-130">Veri bağlamının bir örneği bir "iş birimi" süresine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ecea5-130">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="ecea5-131">Gevşek olarak bağlanmış bir ortamda, bir iş birimi genellikle küçük, tek bir çağrı `SubmitChanges`dahil olmak üzere tek bir iyimser işlem olur.</span><span class="sxs-lookup"><span data-stu-id="ecea5-131">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="ecea5-132">Bu nedenle, veri bağlamı oluşturulup Yöntem kapsamında atılmış olur.</span><span class="sxs-lookup"><span data-stu-id="ecea5-132">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="ecea5-133">Çalışma birimi iş kuralları mantığına çağrılar içeriyorsa, genellikle `DataContext` örneği bu bütün işlem için tutmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ecea5-133">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="ecea5-134">Her durumda, `DataContext` örneklerin rastgele işlem sırasında uzun süreler boyunca etkin tutulması amaçlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="ecea5-134">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="ecea5-135">Bu yöntem, ürün nesnelerini döndürür ancak her ürünle ilişkili Order_Detail nesnelerinin koleksiyonunu değil.</span><span class="sxs-lookup"><span data-stu-id="ecea5-135">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="ecea5-136">Bu varsayılan davranışı değiştirmek için nesnesinikullanın.<xref:System.Data.Linq.DataLoadOptions></span><span class="sxs-lookup"><span data-stu-id="ecea5-136">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="ecea5-137">Daha fazla bilgi için [nasıl yapılır: Ilgili verilerin ne kadar alındığını](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md)denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ecea5-137">For more information, see [How to: Control How Much Related Data Is Retrieved](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="ecea5-138">Veri ekleme</span><span class="sxs-lookup"><span data-stu-id="ecea5-138">Inserting Data</span></span>  
 <span data-ttu-id="ecea5-139">Yeni bir nesne eklemek için sunum katmanı yalnızca orta katman arabirimindeki ilgili yöntemi çağırır ve yeni nesnede eklenecek şekilde geçer.</span><span class="sxs-lookup"><span data-stu-id="ecea5-139">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="ecea5-140">Bazı durumlarda, istemcinin yalnızca bazı değerleri geçmesi ve ortadaki katmanın tam nesneyi oluşturmasına daha etkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-140">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="ecea5-141">Orta katman uygulama</span><span class="sxs-lookup"><span data-stu-id="ecea5-141">Middle Tier Implementation</span></span>  
 <span data-ttu-id="ecea5-142">Orta katmanda yeni <xref:System.Data.Linq.DataContext> bir oluşturulur, <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> nesne <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yöntemi kullanılarak <xref:System.Data.Linq.DataContext> öğesine iliştirilir ve çağrıldığında nesne eklenir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-142">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="ecea5-143">Özel durumlar, geri çağrılar ve hata koşulları diğer Web hizmeti senaryolarında olduğu gibi işlenebilirler.</span><span class="sxs-lookup"><span data-stu-id="ecea5-143">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
```vb  
' No call to Attach is necessary for inserts.  
Public Sub InsertOrder(ByVal o As Order)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    db.Orders.InsertOnSubmit(o)  
  
    ' Exception handling not shown.  
    db.SubmitChanges()  
  
End Sub  
```  
  
```csharp  
// No call to Attach is necessary for inserts.  
    public void InsertOrder(Order o)  
    {  
        NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
        db.Orders.InsertOnSubmit(o);  
  
        // Exception handling not shown.  
        db.SubmitChanges();  
    }  
```  
  
## <a name="deleting-data"></a><span data-ttu-id="ecea5-144">Verileri silme</span><span class="sxs-lookup"><span data-stu-id="ecea5-144">Deleting Data</span></span>  
 <span data-ttu-id="ecea5-145">Veritabanından varolan bir nesneyi silmek için sunum katmanı, ortadaki katman arabirimindeki ilgili yöntemi çağırır ve Silinecek nesnenin orijinal değerlerini içeren kopyasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-145">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="ecea5-146">Silme işlemleri iyimser eşzamanlılık denetimleri içerir ve Silinecek nesnenin önce yeni veri bağlamına bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-146">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="ecea5-147">Bu örnekte, `Boolean` parametresi, nesnesinin zaman damgası ( `false` rowversion) olmadığını belirtmek için olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ecea5-147">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="ecea5-148">Veritabanı tablonuz her kayıt için zaman damgaları üretilemez, eşzamanlılık denetimleri özellikle istemci için çok daha basittir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-148">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="ecea5-149">Yalnızca orijinal veya değiştirilmiş nesneyi geçirin ve `Boolean` parametresini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ecea5-149">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="ecea5-150">Herhangi bir durumda, Orta katmanda genellikle yakalamak <xref:System.Data.Linq.ChangeConflictException>gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-150">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="ecea5-151">İyimser eşzamanlılık çakışmalarını işleme hakkında daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)bakış.</span><span class="sxs-lookup"><span data-stu-id="ecea5-151">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="ecea5-152">İlişkili tablolarda yabancı anahtar kısıtlamalarına sahip varlıkları silerken, önce <xref:System.Data.Linq.EntitySet%601> koleksiyonlarındaki tüm nesneleri silmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-152">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
```vb  
' Attach is necessary for deletes.  
Public Sub DeleteOrder(ByVal order As Order)  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
  
    db.Orders.Attach(order, False)  
    ' This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order)  
  
    Try  
        ' ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict)  
  
    Catch ex As ChangeConflictException  
        ' Get conflict information, and take actions  
        ' that are appropriate for your application.  
        ' See MSDN Article "How to: Manage Change  
        ' Conflicts (LINQ to SQL).  
  
    End Try  
End Sub  
```  
  
```csharp  
// Attach is necessary for deletes.  
public void DeleteOrder(Order order)  
{  
    NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
  
    db.Orders.Attach(order, false);  
    // This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order);  
    try  
    {  
        // ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict);  
    }  
    catch (ChangeConflictException e)  
    {  
       // Get conflict information, and take actions  
       // that are appropriate for your application.  
       // See MSDN Article How to: Manage Change Conflicts (LINQ to SQL).  
    }  
}  
```  
  
## <a name="updating-data"></a><span data-ttu-id="ecea5-153">Verileri güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="ecea5-153">Updating Data</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="ecea5-154">iyimser eşzamanlılık içeren bu senaryolarda güncelleştirmeleri destekler:</span><span class="sxs-lookup"><span data-stu-id="ecea5-154">supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
- <span data-ttu-id="ecea5-155">Zaman damgaları veya RowVersion numaralarına göre iyimser eşzamanlılık.</span><span class="sxs-lookup"><span data-stu-id="ecea5-155">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
- <span data-ttu-id="ecea5-156">Varlık özelliklerinin bir alt kümesinin orijinal değerlerini temel alan iyimser eşzamanlılık.</span><span class="sxs-lookup"><span data-stu-id="ecea5-156">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
- <span data-ttu-id="ecea5-157">Tüm özgün ve değiştirilmiş varlıklar temelinde iyimser eşzamanlılık.</span><span class="sxs-lookup"><span data-stu-id="ecea5-157">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="ecea5-158">Ayrıca, bir varlıkta bir varlık üzerinde güncelleştirmeler veya silmeler, örneğin bir müşteri ve ilişkili sıralama nesnelerinin bir koleksiyonu gibi işlemleri de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecea5-158">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="ecea5-159">İstemcide bir varlık nesneleri ve onların alt (`EntitySet`) koleksiyonları grafiğinde değişiklikler yaptığınızda ve iyimser eşzamanlılık denetimleri orijinal değerler gerektirdiğinde, istemci her varlık için bu özgün değerleri sağlamalıdır ve <xref:System.Data.Linq.EntitySet%601> nesne.</span><span class="sxs-lookup"><span data-stu-id="ecea5-159">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="ecea5-160">İstemcilerinin tek bir yöntem çağrısında ilgili bir dizi ilgili güncelleştirme, silme ve ekleme yapmasını etkinleştirmek istiyorsanız, istemciye her varlıkta ne tür bir işlemin gerçekleştirileceğini belirten bir yol sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-160">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="ecea5-161">Daha sonra, kullanmadan önce her varlık <xref:System.Data.Linq.ITable.Attach%2A> için uygun yöntemi ve sonra <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>veya <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (Eklenenler <xref:System.Data.Linq.DataContext.SubmitChanges%2A>olmadan `Attach`) yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-161">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="ecea5-162">Güncelleştirmeleri denemeden önce özgün değerleri elde etmenin bir yolu olarak veritabanından veri alma.</span><span class="sxs-lookup"><span data-stu-id="ecea5-162">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="ecea5-163">İyimser eşzamanlılık hakkında daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)bakış.</span><span class="sxs-lookup"><span data-stu-id="ecea5-163">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="ecea5-164">İyimser eşzamanlılık değişikliği çakışmalarını çözme hakkında ayrıntılı bilgi için bkz [. nasıl yapılır: Değişiklik çakışmalarını](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)yönetin.</span><span class="sxs-lookup"><span data-stu-id="ecea5-164">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="ecea5-165">Aşağıdaki örneklerde her senaryo gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ecea5-165">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="ecea5-166">Zaman damgalarına sahip iyimser eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="ecea5-166">Optimistic concurrency with timestamps</span></span>  
  
```vb  
' Assume that "customer" has been sent by client.  
' Attach with "true" to say this is a modified entity  
' and it can be checked for optimistic concurrency  
' because it has a column that is marked with the  
' "RowVersion" attribute.  
  
db.Customers.Attach(customer, True)  
  
Try  
    ' Optional: Specify a ConflictMode value  
    ' in call to SubmitChanges.  
    db.SubmitChanges()  
Catch ex As ChangeConflictException  
    ' Handle conflict based on options provided.  
    ' See MSDN article "How to: Manage Change  
    ' Conflicts (LINQ to SQL)".  
End Try  
```  
  
```csharp  
// Assume that "customer" has been sent by client.  
// Attach with "true" to say this is a modified entity  
// and it can be checked for optimistic concurrency because  
//  it has a column that is marked with "RowVersion" attribute  
db.Customers.Attach(customer, true)  
try  
{  
    // Optional: Specify a ConflictMode value  
    // in call to SubmitChanges.  
    db.SubmitChanges();  
}  
catch(ChangeConflictException e)  
{  
    // Handle conflict based on options provided  
    // See MSDN article How to: Manage Change Conflicts (LINQ to SQL).  
}  
```  
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="ecea5-167">Özgün değerlerin alt kümesiyle</span><span class="sxs-lookup"><span data-stu-id="ecea5-167">With Subset of Original Values</span></span>  
 <span data-ttu-id="ecea5-168">Bu yaklaşımda istemci, tüm serileştirilmiş nesneyi, değiştirilecek değerlerle birlikte döndürür.</span><span class="sxs-lookup"><span data-stu-id="ecea5-168">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
```vb  
Public Sub UpdateProductInventory(ByVal p As Product, ByVal _  
    unitsInStock As Short?, ByVal unitsOnOrder As Short?)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        ' p is the original unmodified product  
        ' that was obtained from the database.  
        ' The client kept a copy and returns it now.  
        db.Products.Attach(p, False)  
  
        ' Now that the original values are in the data context,  
        ' apply the changes.  
        p.UnitsInStock = unitsInStock  
        p.UnitsOnOrder = unitsOnOrder  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle conflict based on options provided.  
            ' See MSDN article "How to: Manage Change Conflicts  
            ' (LINQ to SQL)".  
        End Try  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInventory(Product p, short? unitsInStock, short? unitsOnOrder)  
{  
    using (NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString))  
    {  
        // p is the original unmodified product  
        // that was obtained from the database.  
        // The client kept a copy and returns it now.  
        db.Products.Attach(p, false);  
  
        // Now that the original values are in the data context, apply the changes.  
        p.UnitsInStock = unitsInStock;  
        p.UnitsOnOrder = unitsOnOrder;  
        try  
        {  
             // Optional: Specify a ConflictMode value  
             // in call to SubmitChanges.  
             db.SubmitChanges();  
        }  
        catch (ChangeConflictException e)  
        {  
            // Handle conflict based on provided options.  
            // See MSDN article How to: Manage Change Conflicts  
            // (LINQ to SQL).  
        }  
    }  
}  
```  
  
### <a name="with-complete-entities"></a><span data-ttu-id="ecea5-169">Tüm varlıklarla</span><span class="sxs-lookup"><span data-stu-id="ecea5-169">With Complete Entities</span></span>  
  
```vb  
Public Sub UpdateProductInfo(ByVal newProd As Product, ByVal _  
    originalProd As Product)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        db.Products.Attach(newProd, originalProd)  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle potential change conflicgt in whatever way  
            ' is appropriate for your application.  
            ' For more information, see the MSDN article  
            ' "How to: Manage Change Conflicts (LINQ to  
            ' SQL)".  
        End Try  
  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInfo(Product newProd, Product originalProd)  
{  
     using (NorthwindClasses1DataContext db = new  
        NorthwindClasses1DataContext(connectionString))  
     {  
         db.Products.Attach(newProd, originalProd);  
         try  
         {  
               // Optional: Specify a ConflictMode value  
               // in call to SubmitChanges.  
               db.SubmitChanges();  
         }  
        catch (ChangeConflictException e)  
        {  
            // Handle potential change conflict in whatever way  
            // is appropriate for your application.  
            // For more information, see the MSDN article  
            // How to: Manage Change Conflicts (LINQ to SQL)/  
        }   
    }  
}  
```  
  
 <span data-ttu-id="ecea5-170">Bir koleksiyonu güncelleştirmek için <xref:System.Data.Linq.ITable.AttachAll%2A> `Attach`yerine çağırın.</span><span class="sxs-lookup"><span data-stu-id="ecea5-170">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="ecea5-171">Beklenen varlık üyeleri</span><span class="sxs-lookup"><span data-stu-id="ecea5-171">Expected Entity Members</span></span>  
 <span data-ttu-id="ecea5-172">Daha önce belirtildiği gibi, `Attach` yöntemleri çağırmadan önce yalnızca belirli varlık nesnesi üyelerinin ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-172">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="ecea5-173">Ayarlanması gereken varlık üyelerinin aşağıdaki kriterleri yerine getirilmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="ecea5-173">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
- <span data-ttu-id="ecea5-174">Varlığın kimliğinin bir parçası olun.</span><span class="sxs-lookup"><span data-stu-id="ecea5-174">Be part of the entity’s identity.</span></span>  
  
- <span data-ttu-id="ecea5-175">Değiştirilmesi bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="ecea5-175">Be expected to be modified.</span></span>  
  
- <span data-ttu-id="ecea5-176">Bir zaman damgası olun veya <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özniteliği bir `Never`öğe olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ecea5-176">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="ecea5-177">Bir tablo, iyimser eşzamanlılık denetimi için zaman damgası veya sürüm numarası kullanıyorsa, bu üyeleri çağırmadan <xref:System.Data.Linq.ITable.Attach%2A>önce ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-177">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="ecea5-178">Bu sütun özniteliğinde özelliği true olarak ayarlandığında, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> bir üye iyimser eşzamanlılık denetimi için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ecea5-178">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="ecea5-179">İstenen tüm güncelleştirmeler yalnızca sürüm numarası veya zaman damgası değerleri veritabanında aynı ise gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-179">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="ecea5-180">Üye, olarak <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> `Never`ayarlı olmadığı sürece iyimser eşzamanlılık denetiminde de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ecea5-180">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="ecea5-181">Varsayılan değer, başka `Always` bir değer belirtilmemişse olur.</span><span class="sxs-lookup"><span data-stu-id="ecea5-181">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="ecea5-182">Bu gerekli üyelerin herhangi biri eksikse, ("satır bulunamadı <xref:System.Data.Linq.ChangeConflictException> veya değiştirildi" <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ) sırasında bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ecea5-182">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="ecea5-183">Durum</span><span class="sxs-lookup"><span data-stu-id="ecea5-183">State</span></span>  
 <span data-ttu-id="ecea5-184">Bir varlık nesnesi <xref:System.Data.Linq.DataContext> örneğe eklendikten sonra, nesne `PossiblyModified` durumunda olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-184">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="ecea5-185">Eklenmiş bir nesneyi kabul `Modified`etmeye zorlamak için üç yol vardır.</span><span class="sxs-lookup"><span data-stu-id="ecea5-185">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1. <span data-ttu-id="ecea5-186">Bunu değiştirilmemiş olarak ekleyin ve ardından alanları doğrudan değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ecea5-186">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2. <span data-ttu-id="ecea5-187">Geçerli ve orijinal nesne örneklerini alan aşırıyüklemeyeekleyin.<xref:System.Data.Linq.Table%601.Attach%2A></span><span class="sxs-lookup"><span data-stu-id="ecea5-187">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="ecea5-188">Bu değişiklik izleyicisini eski ve yeni değerlerle sağlar, böylece hangi alanların değiştirildiğini otomatik olarak bilir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-188">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3. <span data-ttu-id="ecea5-189">İkinci bir Boole parametresi alan aşırıyüklemeyeekleyin(trueolarakayarlanır).<xref:System.Data.Linq.Table%601.Attach%2A></span><span class="sxs-lookup"><span data-stu-id="ecea5-189">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="ecea5-190">Bu, değişiklik izleyicide herhangi bir özgün değer sağlamak zorunda kalmadan değiştirilen nesneyi kabul edecek şekilde söyleyecektir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-190">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="ecea5-191">Bu yaklaşımda, nesnenin bir sürüm/zaman damgası alanı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecea5-191">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="ecea5-192">Daha fazla bilgi için bkz. [nesne durumları ve değişiklik izleme](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="ecea5-192">For more information, see [Object States and Change-Tracking](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="ecea5-193">Bir varlık nesnesi, iliştirilmekte olan nesneyle aynı kimliğe sahip kimlik önbelleğinde zaten gerçekleşirse, bir <xref:System.Data.Linq.DuplicateKeyException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ecea5-193">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="ecea5-194">Bir `IEnumerable` nesne kümesiyle birlikte eklediğinizde <xref:System.Data.Linq.DuplicateKeyException> , zaten varolan bir anahtar olduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ecea5-194">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="ecea5-195">Kalan nesneler ekli değil.</span><span class="sxs-lookup"><span data-stu-id="ecea5-195">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecea5-196">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecea5-196">See also</span></span>

- [<span data-ttu-id="ecea5-197">LINQ to SQL ile N Katmanı ve Uzak Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="ecea5-197">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
- [<span data-ttu-id="ecea5-198">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="ecea5-198">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
