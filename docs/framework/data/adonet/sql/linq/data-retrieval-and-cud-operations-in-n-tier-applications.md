---
title: N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: 570b3d382157d4be832f57265ad3a064fcd3df9e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743463"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="95835-102">N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="95835-102">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>
<span data-ttu-id="95835-103">Bir ağ üzerinden bir istemci müşteriler veya siparişler gibi varlık nesnelerini seri hale getirmek, bu varlıklar, veri bağlamından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="95835-103">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="95835-104">Veri bağlamı artık değişikliklerini veya diğer nesnelerle ilişkilerini izler.</span><span class="sxs-lookup"><span data-stu-id="95835-104">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="95835-105">İstemcileri yalnızca verileri okumasını sürece, bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="95835-105">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="95835-106">İstemcilerin bir yeni satır eklemek oldukça kolaydır.</span><span class="sxs-lookup"><span data-stu-id="95835-106">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="95835-107">İstemcileri güncelleştirin veya veri silemezsiniz uygulamanız gerekiyorsa çağırmadan önce ancak ardından varlıkları için yeni bir veri bağlamı eklediğiniz gerekir <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="95835-107">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="95835-108">Özgün değerleriyle bir iyimser eşzamanlılık kontrolü kullanıyorsanız, ayrıca, ardından da veritabanı orijinal varlık hem varlık değiştirilmiş olarak sağlamak için bir yol almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="95835-108">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="95835-109">`Attach` Yöntemleri ayrılmış eklendikten sonra yeni bir veri bağlamına varlıkları put olanak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="95835-109">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="95835-110">Proxy nesneleri yerine seri hale getirme bile [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varlıkları devam veri erişim katmanı (DAL) üzerinde bir varlık oluşturun ve yeni bir ekleme <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>veritabanı veri göndermek için.</span><span class="sxs-lookup"><span data-stu-id="95835-110">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="95835-111">varlıkları nasıl serileştirilir hakkında tamamen farklı olur.</span><span class="sxs-lookup"><span data-stu-id="95835-111">is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="95835-112">Windows Communication Foundation (WCF) kullanarak seri hale getirilebilir sınıflar oluşturmak için Nesne İlişkisel Tasarımcısı ve SQLMetal araçlarını kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Varlıkları serileştirilebilir yapmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).</span><span class="sxs-lookup"><span data-stu-id="95835-112">For more information about how to use the Object Relational Designer and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95835-113">Yalnızca çağrı `Attach` yöntemleri yeni veya seri durumdan çıkarılmış varlık.</span><span class="sxs-lookup"><span data-stu-id="95835-113">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="95835-114">Tek bir varlığın özgün veri bağlamından ayrılacak serileştirilmesi için yoludur.</span><span class="sxs-lookup"><span data-stu-id="95835-114">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="95835-115">Undetached bir varlık eklemek için yeni bir veri bağlamı denerseniz ve bu varlığa yine de önceki kendi veri bağlamından yükleyicileri ertelenmiş [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir özel durum olacaktır.</span><span class="sxs-lookup"><span data-stu-id="95835-115">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="95835-116">INSERT, update ve bu varlık üzerinde silme işlemleri gerçekleştirdiğinizde iki farklı veri bağlamları gelen ertelenmiş yükleyici sahip bir varlık istenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="95835-116">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="95835-117">Ertelenmiş Yükleyici hakkında daha fazla bilgi için bkz: [Ertelenen hemen yükleme](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="95835-117">For more information about deferred loaders, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="95835-118">Veri alma</span><span class="sxs-lookup"><span data-stu-id="95835-118">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="95835-119">İstemci yöntem çağrısı</span><span class="sxs-lookup"><span data-stu-id="95835-119">Client Method Call</span></span>  
 <span data-ttu-id="95835-120">Aşağıdaki örnekler, DAL bir Windows Forms istemciden bir örnek yöntem çağrısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="95835-120">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="95835-121">Bu örnekte, bir Windows hizmet kitaplığı DAL uygulanır:</span><span class="sxs-lookup"><span data-stu-id="95835-121">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
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
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="95835-122">Orta katman uygulama</span><span class="sxs-lookup"><span data-stu-id="95835-122">Middle Tier Implementation</span></span>  
 <span data-ttu-id="95835-123">Aşağıdaki örnek, Orta katmanda arabirim yöntemini bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="95835-123">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="95835-124">Unutmayın, iki ana noktaları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="95835-124">The following are the two main points to note:</span></span>  
  
- <span data-ttu-id="95835-125"><xref:System.Data.Linq.DataContext> Yöntemi kapsamda bildirilir.</span><span class="sxs-lookup"><span data-stu-id="95835-125">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
- <span data-ttu-id="95835-126">Yöntem döndürür bir <xref:System.Collections.IEnumerable> gerçek sonuçlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="95835-126">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="95835-127">Seri hale getirici sonuçları istemci/sunu katmanı geri gönderilecek sorgu yürütülür.</span><span class="sxs-lookup"><span data-stu-id="95835-127">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="95835-128">Sorgu sonuçları orta katman üzerinde yerel olarak erişmek için yürütme çağırarak zorlayabilirsiniz `ToList` veya `ToArray` sorgu değişkeni üzerinde.</span><span class="sxs-lookup"><span data-stu-id="95835-128">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="95835-129">Bu listeyi döndürür veya olarak dizi bir `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="95835-129">You can then return that list or array as an `IEnumerable`.</span></span>  
  
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
  
 <span data-ttu-id="95835-130">Bir veri bağlamı örneğini bir "iş birimidir." ömrünü olmalıdır</span><span class="sxs-lookup"><span data-stu-id="95835-130">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="95835-131">Bir iş birimi zamanı gevşek bağlanmış bir ortamda, genellikle küçük, tek bir çağrı dahil olmak üzere belki de bir iyimser işlem `SubmitChanges`.</span><span class="sxs-lookup"><span data-stu-id="95835-131">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="95835-132">Bu nedenle, veri bağlamı oluşturulur ve yöntemi kapsamında atıldı.</span><span class="sxs-lookup"><span data-stu-id="95835-132">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="95835-133">İş kuralları mantığı çağrıları iş birimini içeren sonra genellikle tutmak isteyeceksiniz `DataContext` tüm bu işlem için örneği.</span><span class="sxs-lookup"><span data-stu-id="95835-133">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="95835-134">Her iki durumda da `DataContext` örnekleri amaçlanmayan uzun süreler için rastgele sayıda işlem Canlı tutulması.</span><span class="sxs-lookup"><span data-stu-id="95835-134">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="95835-135">Bu yöntem, ürün nesneler ancak değil her ürünle ilişkilendirilmiş Order_Detail nesneleri koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="95835-135">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="95835-136">Kullanım <xref:System.Data.Linq.DataLoadOptions> bu varsayılan davranışı değiştirmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="95835-136">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="95835-137">Daha fazla bilgi için [nasıl yapılır: Ne kadar ilgili verilerin alındığını denetleme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).</span><span class="sxs-lookup"><span data-stu-id="95835-137">For more information, see [How to: Control How Much Related Data Is Retrieved](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="95835-138">Veri ekleme</span><span class="sxs-lookup"><span data-stu-id="95835-138">Inserting Data</span></span>  
 <span data-ttu-id="95835-139">Yeni bir nesne eklemek için sunu katmanı yalnızca orta katman arabirimde ilgili yöntemi çağırır ve eklemek için yeni nesne geçirir.</span><span class="sxs-lookup"><span data-stu-id="95835-139">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="95835-140">Bazı durumlarda, istemcinin tam nesneyi oluşturmak orta katman vardır ve yalnızca bazı değerleri geçirmek için daha verimli olabilir.</span><span class="sxs-lookup"><span data-stu-id="95835-140">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="95835-141">Orta katman uygulama</span><span class="sxs-lookup"><span data-stu-id="95835-141">Middle Tier Implementation</span></span>  
 <span data-ttu-id="95835-142">Orta katmanda, yeni bir <xref:System.Data.Linq.DataContext> olan oluşturulan nesne bağlı <xref:System.Data.Linq.DataContext> kullanarak <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> yöntemi ve nesnenin ne zaman eklenir <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="95835-142">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="95835-143">Yalnızca tüm diğer Web hizmeti senaryosunda olduğu gibi özel durumlar, geri çağrılar ve hata koşullarını işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="95835-143">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
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
  
## <a name="deleting-data"></a><span data-ttu-id="95835-144">Verileri silme</span><span class="sxs-lookup"><span data-stu-id="95835-144">Deleting Data</span></span>  
 <span data-ttu-id="95835-145">Var olan bir nesne veritabanından silmek için sunu katmanı orta katman arabiriminde ilgili yöntemi çağırır ve Silinecek nesnenin orijinal değerleri içeren kendi kopya geçirir.</span><span class="sxs-lookup"><span data-stu-id="95835-145">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="95835-146">Silme işlemi, iyimser eşzamanlılık denetimlerinin içerir ve silinecek nesne yeni veri bağlamı için önce bağlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="95835-146">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="95835-147">Bu örnekte, `Boolean` parametrenin ayarlanmış `false` nesne bir zaman damgası (RowVersion) sahip olmadığını göstermek için.</span><span class="sxs-lookup"><span data-stu-id="95835-147">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="95835-148">Veritabanı tablonuzun her kayıt için zaman damgaları oluşturursanız, bu eşzamanlılık denetimlerinin özellikle istemci için kadar kolay.</span><span class="sxs-lookup"><span data-stu-id="95835-148">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="95835-149">Yalnızca ya da özgün ya da değiştirilmiş nesnesi içinde geçirin ve ayarlama `Boolean` parametresi `true`.</span><span class="sxs-lookup"><span data-stu-id="95835-149">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="95835-150">Herhangi bir durumda, Orta katmanda genellikle yakalamak gerekli olduğu <xref:System.Data.Linq.ChangeConflictException>.</span><span class="sxs-lookup"><span data-stu-id="95835-150">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="95835-151">İyimser eşzamanlılık çakışmalarını işleme hakkında daha fazla bilgi için bkz. [iyimser eşzamanlılık: Genel Bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="95835-151">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="95835-152">İlişkili tablolardaki yabancı anahtar kısıtlamaları olan varlıkları silmek, tüm nesneleri önce silmeniz gerekir, <xref:System.Data.Linq.EntitySet%601> koleksiyonları.</span><span class="sxs-lookup"><span data-stu-id="95835-152">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
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
  
## <a name="updating-data"></a><span data-ttu-id="95835-153">Verileri güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="95835-153">Updating Data</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="95835-154">İyimser eşzamanlılık içeren bu senaryolarda güncelleştirmeleri destekler:</span><span class="sxs-lookup"><span data-stu-id="95835-154">supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
- <span data-ttu-id="95835-155">Zaman damgaları veya sayıları göre iyimser eşzamanlılık.</span><span class="sxs-lookup"><span data-stu-id="95835-155">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
- <span data-ttu-id="95835-156">Varlık özelliklerinin bir alt özgün değerlerine göre iyimser eşzamanlılık.</span><span class="sxs-lookup"><span data-stu-id="95835-156">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
- <span data-ttu-id="95835-157">İyimser eşzamanlılık tam özgün ve düzeltilmiş varlıkları temel alınarak.</span><span class="sxs-lookup"><span data-stu-id="95835-157">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="95835-158">Bir varlıkta kendi ilişkileri, örneğin bir müşteri ve ilişkili nesnelerini sipariş koleksiyonunu birlikte, güncelleştirme ve silme gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95835-158">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="95835-159">Yaptığınızda değişiklikler istemcide bir grafiğini varlık nesneleri ve onların alt (`EntitySet`) koleksiyonları ve iyimser eşzamanlılık denetimlerini orijinal değerleri gerektirir, istemci her varlık için özgün bu değerler sağlamanız gerekir ve <xref:System.Data.Linq.EntitySet%601> nesne.</span><span class="sxs-lookup"><span data-stu-id="95835-159">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="95835-160">Tek bir yöntem çağrısında bir dizi ilgili güncelleştirmeler, siler ve eklemeler istemcilerin etkinleştirmek istiyorsanız, istemci her varlık üzerinde gerçekleştirilecek işlem türüne göstermek için bir yol sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="95835-160">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="95835-161">Orta katmanda, ardından uygun çağırmalısınız <xref:System.Data.Linq.ITable.Attach%2A> yöntemi ardından <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, veya <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (olmadan `Attach`, eklemeleri için) çağırmadan önce her varlık için <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="95835-161">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="95835-162">Veritabanından bir şekilde güncelleştirmeleri denemeden önce özgün değerlerini almak için veri yok.</span><span class="sxs-lookup"><span data-stu-id="95835-162">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="95835-163">İyimser eşzamanlılık hakkında daha fazla bilgi için bkz: [iyimser eşzamanlılık: Genel Bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="95835-163">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="95835-164">İyimser eşzamanlılık çözme konusunda ayrıntılı bilgi için çakışmaları değiştirmek [nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="95835-164">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="95835-165">Aşağıdaki örnekler, her bir senaryo gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="95835-165">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="95835-166">Zaman damgası ile iyimser eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="95835-166">Optimistic concurrency with timestamps</span></span>  
  
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
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="95835-167">Orijinal değerleri alt kümesi ile</span><span class="sxs-lookup"><span data-stu-id="95835-167">With Subset of Original Values</span></span>  
 <span data-ttu-id="95835-168">Bu yaklaşımda, istemci değiştirilmesi için değerleri ile birlikte tam serileştirilmiş nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="95835-168">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
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
  
### <a name="with-complete-entities"></a><span data-ttu-id="95835-169">Tam varlıklarla</span><span class="sxs-lookup"><span data-stu-id="95835-169">With Complete Entities</span></span>  
  
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
  
 <span data-ttu-id="95835-170">Bir koleksiyonu güncellemek için çağrı <xref:System.Data.Linq.ITable.AttachAll%2A> yerine `Attach`.</span><span class="sxs-lookup"><span data-stu-id="95835-170">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="95835-171">Beklenen varlık üyeleri</span><span class="sxs-lookup"><span data-stu-id="95835-171">Expected Entity Members</span></span>  
 <span data-ttu-id="95835-172">Daha önce belirtildiği gibi varlık nesnesi yalnızca belirli üyeleri çağırmadan önce ayarlamak için gerekli olan `Attach` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="95835-172">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="95835-173">Ayarlanması gereken varlık üyeleri aşağıdaki ölçütleri karşılamalıdır:</span><span class="sxs-lookup"><span data-stu-id="95835-173">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
- <span data-ttu-id="95835-174">Varlığın kimliğinin bir parçası olun.</span><span class="sxs-lookup"><span data-stu-id="95835-174">Be part of the entity’s identity.</span></span>  
  
- <span data-ttu-id="95835-175">Değiştirilecek beklenebilir.</span><span class="sxs-lookup"><span data-stu-id="95835-175">Be expected to be modified.</span></span>  
  
- <span data-ttu-id="95835-176">Bir zaman damgası olmalısınız veya kendi <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özniteliği ayarlanmış yanı sıra bir şey `Never`.</span><span class="sxs-lookup"><span data-stu-id="95835-176">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="95835-177">Bir tablo için bir iyimser eşzamanlılık denetimi bir zaman damgası veya sürüm numarası kullanıyorsa, çağırmadan önce bu üyeler ayarlamalısınız <xref:System.Data.Linq.ITable.Attach%2A>.</span><span class="sxs-lookup"><span data-stu-id="95835-177">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="95835-178">Bir üye için iyimser eşzamanlılık denetimi zaman adanmış <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özelliği bu sütun özniteliği true.</span><span class="sxs-lookup"><span data-stu-id="95835-178">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="95835-179">Yalnızca sürüm numarası veya zaman damgası değerleri aynıysa veritabanında, istenen güncelleştirmeleri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="95835-179">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="95835-180">Üyesi olmadığı sürece üyesi de iyimser eşzamanlılık kontrolü içinde kullanılan <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> kümesine `Never`.</span><span class="sxs-lookup"><span data-stu-id="95835-180">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="95835-181">Varsayılan değer `Always` başka bir değer belirtilirse.</span><span class="sxs-lookup"><span data-stu-id="95835-181">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="95835-182">Bunlardan herhangi birini üyeleri eksikse, gerekirse bir <xref:System.Data.Linq.ChangeConflictException> sırasında oluşturulan <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("satır bulunamadı veya değiştirilen").</span><span class="sxs-lookup"><span data-stu-id="95835-182">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="95835-183">Durum</span><span class="sxs-lookup"><span data-stu-id="95835-183">State</span></span>  
 <span data-ttu-id="95835-184">Nesne sonra bir varlığa bağlı olduğu <xref:System.Data.Linq.DataContext> nesne örneği, kabul olması `PossiblyModified` durumu.</span><span class="sxs-lookup"><span data-stu-id="95835-184">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="95835-185">Bağlı nesneyi kabul zorlamak için üç yol vardır `Modified`.</span><span class="sxs-lookup"><span data-stu-id="95835-185">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1. <span data-ttu-id="95835-186">Değiştirilmemiş olarak ekleme ve doğrudan alanları değiştirin.</span><span class="sxs-lookup"><span data-stu-id="95835-186">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2. <span data-ttu-id="95835-187">Kendisiyle ekleme <xref:System.Data.Linq.Table%601.Attach%2A> geçerli ve özgün nesne örneklerini alan aşırı yüklemesini.</span><span class="sxs-lookup"><span data-stu-id="95835-187">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="95835-188">Değiştirilen alanları otomatik olarak bilir, böylece bu eski ve yeni değerlerle değişikliği İzleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="95835-188">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3. <span data-ttu-id="95835-189">Kendisiyle ekleme <xref:System.Data.Linq.Table%601.Attach%2A> ikinci (true olarak ayarlanırsa) Boolean parametresini alan aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="95835-189">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="95835-190">Bu, herhangi bir özgün değeri sağlamak zorunda kalmadan değiştirilmiş nesne dikkate alınması gereken değişiklik İzleyici bildirir.</span><span class="sxs-lookup"><span data-stu-id="95835-190">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="95835-191">Bu yaklaşımda, nesnenin sürümü/zaman damgası alanı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="95835-191">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="95835-192">Daha fazla bilgi için [nesne durumları ve değişiklik izleme](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="95835-192">For more information, see [Object States and Change-Tracking](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="95835-193">Kimliği önbelleğinde iliştirilmekte, nesne olarak aynı kimliğe sahip bir varlık nesnesine oluşursa bir <xref:System.Data.Linq.DuplicateKeyException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="95835-193">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="95835-194">İle bağladığınızda bir `IEnumerable` nesneler bir <xref:System.Data.Linq.DuplicateKeyException> zaten var olan bir anahtar olmadığı durumlarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="95835-194">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="95835-195">Kalan nesneler bağlı değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="95835-195">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95835-196">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95835-196">See also</span></span>

- [<span data-ttu-id="95835-197">LINQ to SQL ile N Katmanı ve Uzak Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="95835-197">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
- [<span data-ttu-id="95835-198">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="95835-198">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
