---
title: "Veri alma ve CUD işlemleri N katmanlı uygulamalarda (LINQ-SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: adc5d50707155495c43703b6586cedf5da209b69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="3e4da-102">Veri alma ve CUD işlemleri N katmanlı uygulamalarda (LINQ-SQL)</span><span class="sxs-lookup"><span data-stu-id="3e4da-102">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>
<span data-ttu-id="3e4da-103">Bir ağ üzerinden bir istemciye müşteriler veya siparişler gibi varlık nesnesi seri hale olduğunda bu varlıkların kendi veri bağlamından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="3e4da-103">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="3e4da-104">Veri bağlamı artık kendi değişiklikler veya diğer nesnelerle ilişkilendirmelerinin izler.</span><span class="sxs-lookup"><span data-stu-id="3e4da-104">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="3e4da-105">İstemcileri yalnızca verileri okuma sürece, bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="3e4da-105">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="3e4da-106">Bunu ayrıca bir yeni satırları eklemek istemcileri etkinleştirmek oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="3e4da-106">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="3e4da-107">Uygulamanızı istemcileri güncelleştirin veya verilerini silmek mümkün gerektiriyorsa, çağırmadan önce ancak, daha sonra varlıklar için yeni bir veri bağlamı eklemeniz gerekir <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3e4da-107">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3e4da-108">Özgün değerleriyle iyimser eşzamanlılık kontrolü kullanıyorsanız, ek olarak, ardından da veritabanını orijinal varlık ve varlık değiştirilmiş olarak sağlamak için bir yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e4da-108">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="3e4da-109">`Attach` Yöntemleri ayrılmış eklendikten sonra yeni bir veri bağlamına varlıklar put olanak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3e4da-109">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="3e4da-110">Yerine proxy nesneleri seri hale getirme olsa bile [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varlıkları devam veri erişim katmanı'nı (DAL) üzerinde bir varlık oluşturun ve yeni bir eklemek <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>veritabanı veri göndermek için.</span><span class="sxs-lookup"><span data-stu-id="3e4da-110">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="3e4da-111">varlıkları nasıl serileştirilir hakkında tamamen ilgisiz olur.</span><span class="sxs-lookup"><span data-stu-id="3e4da-111"> is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="3e4da-112">Nasıl kullanılacağı hakkında daha fazla bilgi için [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ve Windows Communication Foundation (WCF) kullanarak serileştirilebilir sınıflar oluşturmak için SQLMetal araçları görmek [nasıl yapılır: varlıklar serileştirilebilir olun](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).</span><span class="sxs-lookup"><span data-stu-id="3e4da-112">For more information about how to use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e4da-113">Yalnızca arama `Attach` yeni veya seri durumdan çıkarılmış varlık yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="3e4da-113">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="3e4da-114">Yalnızca kendi özgün veri bağlamından ayrılmış olması bir varlık için seri hale getirilebilmesi için yoludur.</span><span class="sxs-lookup"><span data-stu-id="3e4da-114">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="3e4da-115">Yeni bir veri bağlamı undetached bir varlık eklemek denerseniz ve varlık önceki kendi veri bağlamından yükleyicilerini ertelenmiş [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir özel durum olacaktır.</span><span class="sxs-lookup"><span data-stu-id="3e4da-115">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="3e4da-116">INSERT, update ve bu varlıkta silme işlemleri gerçekleştirdiğinizde iki farklı veri bağlamları gelen ertelenmiş yükleyicilerini sahip bir varlık istenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e4da-116">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="3e4da-117">Ertelenmiş yükleyicilerini hakkında daha fazla bilgi için bkz: [hemen yüklenirken karşı ertelenmiş](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="3e4da-117">For more information about deferred loaders, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="3e4da-118">Veri alma</span><span class="sxs-lookup"><span data-stu-id="3e4da-118">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="3e4da-119">İstemci yöntem çağrısı</span><span class="sxs-lookup"><span data-stu-id="3e4da-119">Client Method Call</span></span>  
 <span data-ttu-id="3e4da-120">Aşağıdaki örnekler bir örnek yöntem çağrısı DAL için bir Windows Forms istemciden gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e4da-120">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="3e4da-121">Bu örnekte, bir Windows hizmet kitaplığı DAL uygulanır:</span><span class="sxs-lookup"><span data-stu-id="3e4da-121">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
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
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="3e4da-122">Orta katman uygulama</span><span class="sxs-lookup"><span data-stu-id="3e4da-122">Middle Tier Implementation</span></span>  
 <span data-ttu-id="3e4da-123">Aşağıdaki örnek arabirimi yöntemin bir uygulaması, Orta katmanda gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e4da-123">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="3e4da-124">Not etmek için iki ana noktalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3e4da-124">The following are the two main points to note:</span></span>  
  
-   <span data-ttu-id="3e4da-125"><xref:System.Data.Linq.DataContext> Yöntemi kapsamda bildirilir.</span><span class="sxs-lookup"><span data-stu-id="3e4da-125">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
-   <span data-ttu-id="3e4da-126">Yöntem bir <xref:System.Collections.IEnumerable> gerçek sonuçları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3e4da-126">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="3e4da-127">Seri hale getirici sonuçları geri istemci/sunu katmanı göndermek için sorgu yürütülür.</span><span class="sxs-lookup"><span data-stu-id="3e4da-127">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="3e4da-128">Sorgu sonuçları orta katman yerel olarak erişmek için yürütme çağırarak zorlayabilirsiniz `ToList` veya `ToArray` sorgu değişkeni üzerinde.</span><span class="sxs-lookup"><span data-stu-id="3e4da-128">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="3e4da-129">Bu liste dönün veya olarak dizi bir `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="3e4da-129">You can then return that list or array as an `IEnumerable`.</span></span>  
  
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
  
 <span data-ttu-id="3e4da-130">Bir veri bağlamı örneğini bir "iş birimidir." ömrü olmalıdır</span><span class="sxs-lookup"><span data-stu-id="3e4da-130">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="3e4da-131">Gevşek bağlanmış bir ortamda, bir iş birimine genellikle küçük, tek bir çağrı dahil olmak üzere belki de bir iyimser hareket `SubmitChanges`.</span><span class="sxs-lookup"><span data-stu-id="3e4da-131">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="3e4da-132">Bu nedenle, veri bağlamı oluşturulur ve yöntemi kapsamda atıldı.</span><span class="sxs-lookup"><span data-stu-id="3e4da-132">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="3e4da-133">İş kuralları mantığı çağrıları iş birimini içeren sonra genellikle tutmak isteyeceksiniz `DataContext` tüm bu işlem için örneği.</span><span class="sxs-lookup"><span data-stu-id="3e4da-133">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="3e4da-134">Her iki durumda da `DataContext` örnekleri amaçlanmayan uzun süreler için işlemleri rastgele sayılar arasında Canlı tutulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e4da-134">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="3e4da-135">Bu yöntem ürün nesneler ancak değil her ürünüyle ilişkilendirilen Order_Detail nesneler koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e4da-135">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="3e4da-136">Kullanım <xref:System.Data.Linq.DataLoadOptions> bu varsayılan davranışı değiştirmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="3e4da-136">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="3e4da-137">Daha fazla bilgi için bkz: [nasıl yapılır: denetim nasıl çok ilgili veriler alınır](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).</span><span class="sxs-lookup"><span data-stu-id="3e4da-137">For more information, see [How to: Control How Much Related Data Is Retrieved](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="3e4da-138">Veri ekleme</span><span class="sxs-lookup"><span data-stu-id="3e4da-138">Inserting Data</span></span>  
 <span data-ttu-id="3e4da-139">Yeni bir nesne eklemek için sunu katmanı yalnızca orta katman arabirimde ilgili yöntemini çağırır ve eklemek için yeni nesne geçirir.</span><span class="sxs-lookup"><span data-stu-id="3e4da-139">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="3e4da-140">Bazı durumlarda, tam nesne oluşturmak orta katman yalnızca bazı değerleri geçirmek ve istemci için daha etkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e4da-140">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="3e4da-141">Orta katman uygulama</span><span class="sxs-lookup"><span data-stu-id="3e4da-141">Middle Tier Implementation</span></span>  
 <span data-ttu-id="3e4da-142">Orta katman yeni bir <xref:System.Data.Linq.DataContext> olan oluşturulan nesneyi bağlı <xref:System.Data.Linq.DataContext> kullanarak <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> yöntemi ve nesne zaman eklenir <xref:System.Data.Linq.DataContext.SubmitChanges%2A> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3e4da-142">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="3e4da-143">Özel durumlar, geri çağrılar ve hata koşulları yalnızca herhangi diğer Web Hizmetleri senaryosu olduğu gibi işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3e4da-143">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
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
  
## <a name="deleting-data"></a><span data-ttu-id="3e4da-144">Verileri silme</span><span class="sxs-lookup"><span data-stu-id="3e4da-144">Deleting Data</span></span>  
 <span data-ttu-id="3e4da-145">Varolan bir nesne veritabanından silmek için sunu katmanı orta katman arabirimde ilgili yöntemini çağırır ve Silinecek nesnenin orijinal değerleri içerir, kopyada geçirir.</span><span class="sxs-lookup"><span data-stu-id="3e4da-145">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="3e4da-146">Silme işlemleri iyimser eşzamanlılık denetimleri içerir ve Silinecek nesnenin yeni veri bağlamı için öncelikle bağlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e4da-146">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="3e4da-147">Bu örnekte, `Boolean` parametrenin ayarlanmış `false` nesne zaman damgası (RowVersion) sahip olup olmadığını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="3e4da-147">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="3e4da-148">Veritabanı tablonuza damgaları her kayıt için oluşturursanız, bu eşzamanlılık denetimleri özellikle istemci için daha kolay.</span><span class="sxs-lookup"><span data-stu-id="3e4da-148">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="3e4da-149">Yalnızca ya da özgün ya da değiştirilmiş nesne geçirmek ve ayarlamak `Boolean` parametresi `true`.</span><span class="sxs-lookup"><span data-stu-id="3e4da-149">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="3e4da-150">Her iki durumda da Orta katmanda yakalamak genellikle ise gerekli <xref:System.Data.Linq.ChangeConflictException>.</span><span class="sxs-lookup"><span data-stu-id="3e4da-150">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="3e4da-151">İyimser eşzamanlılık çakışmalarına hakkında daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e4da-151">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="3e4da-152">İlişkili tabloları yabancı anahtar kısıtlamaları olan varlıkları silmek, tüm nesneleri silmeniz gerekir, <xref:System.Data.Linq.EntitySet%601> koleksiyonları.</span><span class="sxs-lookup"><span data-stu-id="3e4da-152">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
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
  
## <a name="updating-data"></a><span data-ttu-id="3e4da-153">Verileri güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="3e4da-153">Updating Data</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="3e4da-154">güncelleştirmeleri iyimser eşzamanlılık içeren bu senaryolarda destekler:</span><span class="sxs-lookup"><span data-stu-id="3e4da-154"> supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
-   <span data-ttu-id="3e4da-155">İyimser eşzamanlılık zaman damgaları veya RowVersion numaraları bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e4da-155">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
-   <span data-ttu-id="3e4da-156">İyimser eşzamanlılık varlık özelliklerinin bir alt özgün değerlerine göre.</span><span class="sxs-lookup"><span data-stu-id="3e4da-156">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
-   <span data-ttu-id="3e4da-157">İyimser eşzamanlılık üzerinde tam özgün ve değiştirilen varlıklar tabanlı.</span><span class="sxs-lookup"><span data-stu-id="3e4da-157">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="3e4da-158">Örneğin bir müşteri ve ilişkili sipariş nesnelerini koleksiyonu kendi ilişkileri ile birlikte bir varlıkta güncelleştirme veya silme de gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e4da-158">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="3e4da-159">Yaptığınızda değişiklikleri istemcide varlık nesneler ve onların alt grafiğe (`EntitySet`) koleksiyonlar ve iyimser eşzamanlılık denetimleri gerektiren özgün değerler, her bir varlık için istemci bu özgün değerler sağlamanız gerekir ve <xref:System.Data.Linq.EntitySet%601> nesne.</span><span class="sxs-lookup"><span data-stu-id="3e4da-159">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="3e4da-160">İstemcilerin bir dizi ilgili güncelleştirmeler, siler ve eklemeleri tek yöntemi çağırmaya izin vermek istiyorsanız, istemci her varlık üzerinde gerçekleştirilecek işlem türünü belirtmek için bir yol sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="3e4da-160">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="3e4da-161">Orta katmanda, ardından uygun çağırmalısınız <xref:System.Data.Linq.ITable.Attach%2A> yöntemi ve ardından <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, veya <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (olmadan `Attach`, eklemeleri için) çağırmadan önce her bir varlık için <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e4da-161">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="3e4da-162">Veritabanından güncelleştirmeleri denemeden önce özgün değerler elde etmenin bir yolu verileri değil.</span><span class="sxs-lookup"><span data-stu-id="3e4da-162">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="3e4da-163">İyimser eşzamanlılık hakkında daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e4da-163">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="3e4da-164">Değiştirme çakışmaları iyimser eşzamanlılık çözme konusunda ayrıntılı bilgi için bkz: [nasıl yapılır: değiştirme çakışmaları yönetmek](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="3e4da-164">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="3e4da-165">Aşağıdaki örnekler, her bir senaryo gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3e4da-165">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="3e4da-166">Zaman damgalı iyimser eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="3e4da-166">Optimistic concurrency with timestamps</span></span>  
  
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
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="3e4da-167">Özgün değerleri alt kümesiyle</span><span class="sxs-lookup"><span data-stu-id="3e4da-167">With Subset of Original Values</span></span>  
 <span data-ttu-id="3e4da-168">Bu yaklaşımda, istemci değerlerin değiştirilmesi birlikte tam serileştirilmiş nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e4da-168">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
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
  
### <a name="with-complete-entities"></a><span data-ttu-id="3e4da-169">Tam varlıklarıyla</span><span class="sxs-lookup"><span data-stu-id="3e4da-169">With Complete Entities</span></span>  
  
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
  
 <span data-ttu-id="3e4da-170">Bir koleksiyonu güncellemek için çağrı <xref:System.Data.Linq.ITable.AttachAll%2A> yerine `Attach`.</span><span class="sxs-lookup"><span data-stu-id="3e4da-170">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="3e4da-171">Beklenen varlık üyeleri</span><span class="sxs-lookup"><span data-stu-id="3e4da-171">Expected Entity Members</span></span>  
 <span data-ttu-id="3e4da-172">Daha önce belirtildiği gibi yalnızca varlık nesnesi belirli üyeleri çağırmadan önce ayarlamak için gerekli olan `Attach` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="3e4da-172">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="3e4da-173">Ayarlanması gereken varlık üyeleri aşağıdaki ölçütleri yerine getirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="3e4da-173">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
-   <span data-ttu-id="3e4da-174">Varlığın kimliğini bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="3e4da-174">Be part of the entity’s identity.</span></span>  
  
-   <span data-ttu-id="3e4da-175">Değiştirilecek beklenen.</span><span class="sxs-lookup"><span data-stu-id="3e4da-175">Be expected to be modified.</span></span>  
  
-   <span data-ttu-id="3e4da-176">Bir zaman damgası olmalısınız veya kendi <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özniteliği kümesine yanı sıra bir şey `Never`.</span><span class="sxs-lookup"><span data-stu-id="3e4da-176">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="3e4da-177">Bir tablo iyimser eşzamanlılık kontrolü için bir zaman damgası veya sürüm numarasını kullanıyorsa, arama yapmadan önce bu üyeler ayarlamalısınız <xref:System.Data.Linq.ITable.Attach%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e4da-177">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="3e4da-178">Üyesi olduğunda denetimi iyimser eşzamanlılık ayrılmış <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özelliği ayarlanmış bu sütun özniteliği true.</span><span class="sxs-lookup"><span data-stu-id="3e4da-178">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="3e4da-179">Yalnızca sürüm numarasını veya zaman damgası değerlerini veritabanında aynıysa istenen güncelleştirmeleri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="3e4da-179">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="3e4da-180">Üye sahip olmadığı sürece üyesi de iyimser eşzamanlılık kontrolü kullanılan <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> kümesine `Never`.</span><span class="sxs-lookup"><span data-stu-id="3e4da-180">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="3e4da-181">Varsayılan değer `Always` başka bir değer belirtilmişse.</span><span class="sxs-lookup"><span data-stu-id="3e4da-181">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="3e4da-182">Bunlardan herhangi bir üye eksik, gerekirse bir <xref:System.Data.Linq.ChangeConflictException> sırasında oluşturulan <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("satır bulunamadı veya değiştirilen").</span><span class="sxs-lookup"><span data-stu-id="3e4da-182">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="3e4da-183">Durum</span><span class="sxs-lookup"><span data-stu-id="3e4da-183">State</span></span>  
 <span data-ttu-id="3e4da-184">Sonra bir varlık nesnesini bağlı <xref:System.Data.Linq.DataContext> örneği, nesne olarak kabul olması `PossiblyModified` durumu.</span><span class="sxs-lookup"><span data-stu-id="3e4da-184">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="3e4da-185">Kabul edilmesi için iliştirilmiş bir nesne zorlamak için üç yolla `Modified`.</span><span class="sxs-lookup"><span data-stu-id="3e4da-185">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1.  <span data-ttu-id="3e4da-186">Değiştirilmemiş olarak ekleyin ve doğrudan alanları değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3e4da-186">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2.  <span data-ttu-id="3e4da-187">İle ekleme <xref:System.Data.Linq.Table%601.Attach%2A> aşırı geçerli ve özgün nesne örneklerini alır.</span><span class="sxs-lookup"><span data-stu-id="3e4da-187">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="3e4da-188">Bu otomatik olarak hangi alanların değişmiş bilmesini bu eski ve yeni değerlerle değişikliği İzleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e4da-188">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3.  <span data-ttu-id="3e4da-189">İle ekleme <xref:System.Data.Linq.Table%601.Attach%2A> ikinci Boolean parametresini (true olarak ayarlanmış) alan aşırı.</span><span class="sxs-lookup"><span data-stu-id="3e4da-189">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="3e4da-190">Bu, tüm özgün değerler sağlamak zorunda kalmadan değiştirilmiş nesne dikkate alınması gereken değişikliği İzleyicisi söyler.</span><span class="sxs-lookup"><span data-stu-id="3e4da-190">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="3e4da-191">Bu yaklaşımda, nesnenin sürümü/zaman damgası alanı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e4da-191">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="3e4da-192">Daha fazla bilgi için bkz: [nesne durumlarını ve değişiklik izleme](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="3e4da-192">For more information, see [Object States and Change-Tracking](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="3e4da-193">Kimliği önbelleğinde iliştirilmekte, nesne aynı kimliğe sahip bir varlık nesnesine oluşursa bir <xref:System.Data.Linq.DuplicateKeyException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3e4da-193">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="3e4da-194">Ne zaman attach ile birlikte bir `IEnumerable` bir nesne, bir <xref:System.Data.Linq.DuplicateKeyException> zaten mevcut bir anahtarı mevcut olduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3e4da-194">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="3e4da-195">Kalan nesneler eklenmemiş.</span><span class="sxs-lookup"><span data-stu-id="3e4da-195">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e4da-196">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3e4da-196">See Also</span></span>  
 [<span data-ttu-id="3e4da-197">N katmanlı ve uzak uygulamalarla LINQ-SQL</span><span class="sxs-lookup"><span data-stu-id="3e4da-197">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [<span data-ttu-id="3e4da-198">Arka plan bilgileri</span><span class="sxs-lookup"><span data-stu-id="3e4da-198">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
