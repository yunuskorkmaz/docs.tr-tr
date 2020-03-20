---
title: N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: 5ab829993b8f8faa6dcb91d3f23e8442b8aa95bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148419"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="82469-102">N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="82469-102">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>
<span data-ttu-id="82469-103">Müşteri veya Siparişler gibi varlık nesnelerini bir ağ üzerinden istemciye serihale ettiğinizde, bu varlıklar veri bağlamından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="82469-103">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="82469-104">Veri bağlamı artık değişikliklerini veya diğer nesnelerle ilişkilendirmelerini izletmez.</span><span class="sxs-lookup"><span data-stu-id="82469-104">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="82469-105">İstemciler yalnızca verileri okuduğu sürece bu bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="82469-105">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="82469-106">İstemcilerin veritabanına yeni satırlar eklemesini sağlamak da nispeten basittir.</span><span class="sxs-lookup"><span data-stu-id="82469-106">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="82469-107">Ancak, uygulamanız istemcilerin verileri güncelleştirebilmelerini veya silebilmelerini gerektiriyorsa, aramadan <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>önce varlıkları yeni bir veri bağlamına iliştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="82469-107">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="82469-108">Buna ek olarak, özgün değerlerle iyimser bir eşzamanlılık denetimi kullanıyorsanız, veritabanını hem özgün varlığı hem de varlığı değiştirilmiş olarak sağlamanın bir yolunu da emegerekir.</span><span class="sxs-lookup"><span data-stu-id="82469-108">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="82469-109">Yöntemler, `Attach` varlıkları ayrıldıktan sonra yeni bir veri bağlamına koymanızı sağlamak için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="82469-109">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="82469-110">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Varlıkların yerine proxy nesnelerini seri hale getirmeniz olsa bile, verileri veritabanına göndermek için veri erişim katmanında <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>(DAL) bir varlık oluşturmanız ve yeni bir ,'ye eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="82469-110">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="82469-111">varlıkların nasıl seri hale getirilen hakkında tamamen kayıtsız.</span><span class="sxs-lookup"><span data-stu-id="82469-111">is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="82469-112">Windows Communication Foundation (WCF) kullanarak serileştirilebilir sınıflar oluşturmak için Object İlişkisel Tasarımcı ve SQLMetal araçlarının nasıl kullanılacağı hakkında daha fazla bilgi için [bkz.](how-to-make-entities-serializable.md)</span><span class="sxs-lookup"><span data-stu-id="82469-112">For more information about how to use the Object Relational Designer and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82469-113">Yalnızca yeni `Attach` veya deserialized varlıklar üzerindeki yöntemleri arayın.</span><span class="sxs-lookup"><span data-stu-id="82469-113">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="82469-114">Bir varlığın özgün veri bağlamından ayrılmasının tek yolu seri hale getirilmesidir.</span><span class="sxs-lookup"><span data-stu-id="82469-114">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="82469-115">Yeni bir veri bağlamına ayrılmamış bir varlık eklemeye çalışırsanız ve bu varlık hala [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] önceki veri bağlamından ertelenmiş yükleyicileri varsa, bir özel durum atacaktır.</span><span class="sxs-lookup"><span data-stu-id="82469-115">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="82469-116">İki farklı veri bağlamından ertelenmiş yükleyicilere sahip bir varlık, bu varlıktaki ekleme, güncelleştirme ve silme işlemlerini gerçekleştirdiğiniz zaman istenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="82469-116">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="82469-117">Ertelenmiş yükleyiciler hakkında daha fazla bilgi için [Ertelenmiş ve Hemen Yükleme](deferred-versus-immediate-loading.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="82469-117">For more information about deferred loaders, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="82469-118">Veri Alma</span><span class="sxs-lookup"><span data-stu-id="82469-118">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="82469-119">İstemci Yöntemi Çağrısı</span><span class="sxs-lookup"><span data-stu-id="82469-119">Client Method Call</span></span>  
 <span data-ttu-id="82469-120">Aşağıdaki örnekler, bir Windows Forms istemcisinden DAL'ye örnek bir yöntem çağrısı gösterir.</span><span class="sxs-lookup"><span data-stu-id="82469-120">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="82469-121">Bu örnekte, DAL Bir Windows Hizmet Kitaplığı olarak uygulanır:</span><span class="sxs-lookup"><span data-stu-id="82469-121">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
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
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="82469-122">Orta Katman Uygulaması</span><span class="sxs-lookup"><span data-stu-id="82469-122">Middle Tier Implementation</span></span>  
 <span data-ttu-id="82469-123">Aşağıdaki örnekte, arabirim yönteminin orta katmanda bir uygulaması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="82469-123">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="82469-124">Dikkat edilmesi gereken iki ana nokta şunlardır:</span><span class="sxs-lookup"><span data-stu-id="82469-124">The following are the two main points to note:</span></span>  
  
- <span data-ttu-id="82469-125">Yöntem <xref:System.Data.Linq.DataContext> kapsamında bildirilir.</span><span class="sxs-lookup"><span data-stu-id="82469-125">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
- <span data-ttu-id="82469-126">Yöntem, gerçek <xref:System.Collections.IEnumerable> sonuçların bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="82469-126">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="82469-127">Serileştirici, sonuçları istemci/sunu katmanına geri göndermek için sorguyu yürütecektir.</span><span class="sxs-lookup"><span data-stu-id="82469-127">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="82469-128">Sorgu sonuçlarına orta katmandaki yerel olarak erişmek için, `ToList` `ToArray` sorgu değişkenini arayarak veya sorgu değişkenini kullanarak yürütmeyi zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82469-128">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="82469-129">Daha sonra bu listeyi veya `IEnumerable`diziyi bir .</span><span class="sxs-lookup"><span data-stu-id="82469-129">You can then return that list or array as an `IEnumerable`.</span></span>  
  
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
  
 <span data-ttu-id="82469-130">Bir veri bağlamı örneğinin bir "çalışma birimi" ömrü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="82469-130">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="82469-131">Gevşek bir leştiği ortamda, bir iş birimi genellikle küçük, belki de tek bir çağrı `SubmitChanges`da dahil olmak üzere iyimser bir işlem.</span><span class="sxs-lookup"><span data-stu-id="82469-131">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="82469-132">Bu nedenle, veri bağlamı oluşturulur ve yöntem kapsamında atılır.</span><span class="sxs-lookup"><span data-stu-id="82469-132">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="82469-133">Çalışma birimi iş kuralları mantığına çağrılar içeriyorsa, genellikle `DataContext` bu tüm işlem için örnek tutmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="82469-133">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="82469-134">Her durumda, `DataContext` örneklerin rasgele sayıda hareket arasında uzun süre canlı tutulması amaçlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="82469-134">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="82469-135">Bu yöntem, Ürün nesnelerini döndürecek, ancak her Ürünle ilişkili Order_Detail nesnelerin inkisini döndürmez.</span><span class="sxs-lookup"><span data-stu-id="82469-135">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="82469-136">Bu <xref:System.Data.Linq.DataLoadOptions> varsayılan davranışı değiştirmek için nesneyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="82469-136">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="82469-137">Daha fazla bilgi için bkz: İlgili Verilerin Ne Kadar ını [Denetle.](how-to-control-how-much-related-data-is-retrieved.md)</span><span class="sxs-lookup"><span data-stu-id="82469-137">For more information, see [How to: Control How Much Related Data Is Retrieved](how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="82469-138">Veri ekleme</span><span class="sxs-lookup"><span data-stu-id="82469-138">Inserting Data</span></span>  
 <span data-ttu-id="82469-139">Yeni bir nesne eklemek için sunu katmanı yalnızca orta katman arabiriminde ilgili yöntemi çağırır ve eklemek için yeni nesnegeçer.</span><span class="sxs-lookup"><span data-stu-id="82469-139">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="82469-140">Bazı durumlarda, istemcinin yalnızca bazı değerleri geçirmesi ve orta katmanın tam nesneyi oluşturmasını sağlamak daha verimli olabilir.</span><span class="sxs-lookup"><span data-stu-id="82469-140">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="82469-141">Orta Katman Uygulaması</span><span class="sxs-lookup"><span data-stu-id="82469-141">Middle Tier Implementation</span></span>  
 <span data-ttu-id="82469-142">Orta katmanda, yeni <xref:System.Data.Linq.DataContext> bir oluşturulur, nesne <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> yöntem kullanılarak eklenir ve çağrıldığında <xref:System.Data.Linq.DataContext.SubmitChanges%2A> nesne eklenir.</span><span class="sxs-lookup"><span data-stu-id="82469-142">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="82469-143">Özel durumlar, geri aramalar ve hata koşulları, diğer Web hizmeti senaryolarında olduğu gibi işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="82469-143">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
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
  
## <a name="deleting-data"></a><span data-ttu-id="82469-144">Veri silme</span><span class="sxs-lookup"><span data-stu-id="82469-144">Deleting Data</span></span>  
 <span data-ttu-id="82469-145">Varolan bir nesneyi veritabanından silmek için, sunu katmanı orta katman arabirimindeki ilgili yöntemi çağırır ve silinecek nesnenin özgün değerlerini içeren kopyasına geçer.</span><span class="sxs-lookup"><span data-stu-id="82469-145">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="82469-146">Silme işlemleri iyimser eşzamanlılık denetimleri içerir ve silinecek nesnenin önce yeni veri bağlamına eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="82469-146">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="82469-147">Bu örnekte, `Boolean` parametre nesnenin bir zaman damgası (RowVersion) olmadığını belirtmek için `false` ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="82469-147">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="82469-148">Veritabanı tablonuz her kayıt için zaman damgaları oluşturuyorsa, eşzamanlılık denetimleri özellikle istemci için çok daha basittir.</span><span class="sxs-lookup"><span data-stu-id="82469-148">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="82469-149">Orijinal veya değiştirilmiş nesneyi geçirin `Boolean` ve parametreyi 'ye `true`ayarlayın</span><span class="sxs-lookup"><span data-stu-id="82469-149">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="82469-150">Her durumda, orta katmanda genellikle yakalamak için <xref:System.Data.Linq.ChangeConflictException>gereklidir.</span><span class="sxs-lookup"><span data-stu-id="82469-150">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="82469-151">İyimser eşzamanlılık çakışmaları hakkında daha fazla bilgi için [Bkz. İyimser Eşzamanlılık: Genel Bakış.](optimistic-concurrency-overview.md)</span><span class="sxs-lookup"><span data-stu-id="82469-151">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="82469-152">İlişkili tablolarda yabancı anahtar kısıtlamaları olan varlıkları silerken, önce <xref:System.Data.Linq.EntitySet%601> koleksiyonlarındaki tüm nesneleri silmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="82469-152">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
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
  
## <a name="updating-data"></a><span data-ttu-id="82469-153">Verileri Güncelleme</span><span class="sxs-lookup"><span data-stu-id="82469-153">Updating Data</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="82469-154">iyimser eşzamanlılık içeren bu senaryolarda güncelleştirmeleri destekler:</span><span class="sxs-lookup"><span data-stu-id="82469-154">supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
- <span data-ttu-id="82469-155">Zaman damgaları veya RowVersion numaralarına dayalı iyimser eşzamanlılık.</span><span class="sxs-lookup"><span data-stu-id="82469-155">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
- <span data-ttu-id="82469-156">Varlık özellikleri alt kümesinin özgün değerlerine dayalı iyimser eşzamanlılık.</span><span class="sxs-lookup"><span data-stu-id="82469-156">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
- <span data-ttu-id="82469-157">Orijinal ve değiştirilmiş varlıkların tamamına dayalı iyimser eşzamanlılık.</span><span class="sxs-lookup"><span data-stu-id="82469-157">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="82469-158">Müşteri ve ilişkili Sipariş nesnelerinin bir koleksiyonu gibi, bir varlık üzerindeki güncelleştirmeleri veya silmeleri ilişkileriyle birlikte de gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82469-158">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="82469-159">Varlık nesneleri ve alt ( )`EntitySet`koleksiyonlarının grafiğinde istemci üzerinde değişiklikler yaptığınızda ve iyimser eşzamanlılık denetimleri özgün değerler gerektiriyorsa, istemci her varlık ve <xref:System.Data.Linq.EntitySet%601> nesne için bu özgün değerleri sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="82469-159">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="82469-160">İstemcilerin tek bir yöntem çağrısında ilgili güncelleştirmeler, silmeler ve eklemeler kümesi yapmasını sağlamak istiyorsanız, istemciye her varlıkta ne tür bir işlem gerçekleştireceklerini belirtmek için bir yol sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="82469-160">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="82469-161">Orta katmanda, daha sonra, <xref:System.Data.Linq.ITable.Attach%2A> aramadan <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>önce <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>her <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> varlık `Attach`için uygun yöntemi aramanız ve <xref:System.Data.Linq.DataContext.SubmitChanges%2A>ardından , veya (eklemeler için olmadan) aramanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="82469-161">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="82469-162">Güncelleştirmeleri denemeden önce özgün değerleri elde etmek için veritabanından veri almayın.</span><span class="sxs-lookup"><span data-stu-id="82469-162">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="82469-163">İyimser eşzamanlılık hakkında daha fazla bilgi için, [Bkz. İyimser Eşzamanlılık: Genel Bakış.](optimistic-concurrency-overview.md)</span><span class="sxs-lookup"><span data-stu-id="82469-163">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="82469-164">İyimser eşzamanlılık değişikliği çakışmalarını çözme hakkında ayrıntılı bilgi için [bkz.](how-to-manage-change-conflicts.md)</span><span class="sxs-lookup"><span data-stu-id="82469-164">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="82469-165">Aşağıdaki örnekler her senaryoyu gösterir:</span><span class="sxs-lookup"><span data-stu-id="82469-165">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="82469-166">Zaman damgaları ile iyimser eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="82469-166">Optimistic concurrency with timestamps</span></span>  
  
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
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="82469-167">Orijinal Değerlerin Alt Kümesi ile</span><span class="sxs-lookup"><span data-stu-id="82469-167">With Subset of Original Values</span></span>  
 <span data-ttu-id="82469-168">Bu yaklaşımda, istemci değiştirilecek değerlerle birlikte serileştirilmiş nesnenin tamamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="82469-168">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
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
  
### <a name="with-complete-entities"></a><span data-ttu-id="82469-169">Komple Varlıklarla</span><span class="sxs-lookup"><span data-stu-id="82469-169">With Complete Entities</span></span>  
  
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
  
 <span data-ttu-id="82469-170">Koleksiyonu güncelleştirmek için, `Attach`"' yerine çağırın. <xref:System.Data.Linq.ITable.AttachAll%2A></span><span class="sxs-lookup"><span data-stu-id="82469-170">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="82469-171">Beklenen Varlık Üyeleri</span><span class="sxs-lookup"><span data-stu-id="82469-171">Expected Entity Members</span></span>  
 <span data-ttu-id="82469-172">Daha önce belirtildiği gibi, `Attach` yöntemleri çağırmadan önce yalnızca belirli varlık nesnesinin üyelerinin ayarlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82469-172">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="82469-173">Ayarlanılması gereken varlık üyeleri aşağıdaki ölçütleri karşılamalıdır:</span><span class="sxs-lookup"><span data-stu-id="82469-173">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
- <span data-ttu-id="82469-174">Varlığın kimliğinin bir parçası olun.</span><span class="sxs-lookup"><span data-stu-id="82469-174">Be part of the entity’s identity.</span></span>  
  
- <span data-ttu-id="82469-175">Değiştirilmesi bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="82469-175">Be expected to be modified.</span></span>  
  
- <span data-ttu-id="82469-176">Bir zaman damgası <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> olun veya özniteliği `Never`yanında bir şey ayarlanmış olması.</span><span class="sxs-lookup"><span data-stu-id="82469-176">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="82469-177">Bir tablo iyimser bir eşzamanlılık denetimi için bir zaman damgası veya sürüm <xref:System.Data.Linq.ITable.Attach%2A>numarası kullanıyorsa, bu üyeleri aramadan önce ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="82469-177">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="82469-178">Bir üye, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özellik bu Sütun özniteliği üzerinde doğru ayarlandığında iyimser eşzamanlılık denetimi için adamıştır.</span><span class="sxs-lookup"><span data-stu-id="82469-178">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="82469-179">İstenen güncelleştirmeler yalnızca sürüm numarası veya zaman damgası değerleri veritabanında aynıysa gönderilir.</span><span class="sxs-lookup"><span data-stu-id="82469-179">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="82469-180">Bir üye, iyimser eşzamanlılık denetiminde de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> `Never`kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82469-180">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="82469-181">Varsayılan değer, `Always` başka bir değer belirtilmemişse değerdir.</span><span class="sxs-lookup"><span data-stu-id="82469-181">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="82469-182">Bu gerekli üyelerden herhangi biri <xref:System.Data.Linq.ChangeConflictException> eksikse, bir satır ("Satır bulunamadı veya değiştirilmez") sırasında <xref:System.Data.Linq.DataContext.SubmitChanges%2A> atılır.</span><span class="sxs-lookup"><span data-stu-id="82469-182">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="82469-183">Durum</span><span class="sxs-lookup"><span data-stu-id="82469-183">State</span></span>  
 <span data-ttu-id="82469-184">Bir varlık nesnesi <xref:System.Data.Linq.DataContext> örneğe iliştirildikten sonra, nesne `PossiblyModified` durumda olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="82469-184">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="82469-185">Ekli bir nesneyi dikkate `Modified`almaya zorlamanın üç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="82469-185">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1. <span data-ttu-id="82469-186">Değiştirilmemiş olarak takın ve sonra alanları doğrudan değiştirin.</span><span class="sxs-lookup"><span data-stu-id="82469-186">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2. <span data-ttu-id="82469-187">Geçerli ve <xref:System.Data.Linq.Table%601.Attach%2A> özgün nesne örneklerini alan aşırı yükletin.</span><span class="sxs-lookup"><span data-stu-id="82469-187">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="82469-188">Bu, hangi alanların değiştiğini otomatik olarak bilecek şekilde değişim izleyicisini eski ve yeni değerlerle birlikte sağlar.</span><span class="sxs-lookup"><span data-stu-id="82469-188">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3. <span data-ttu-id="82469-189">İkinci bir <xref:System.Data.Linq.Table%601.Attach%2A> Boolean parametresi (doğru ayarlanmış) alır aşırı yük ile takın.</span><span class="sxs-lookup"><span data-stu-id="82469-189">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="82469-190">Bu, değişiklik izleyicisine, özgün değerler sağlamak zorunda kalmadan nesneyi değiştirildiğini düşünmesini söyler.</span><span class="sxs-lookup"><span data-stu-id="82469-190">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="82469-191">Bu yaklaşımda, nesnenin bir sürüm/zaman damgası alanı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="82469-191">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="82469-192">Daha fazla bilgi için [bkz.](object-states-and-change-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="82469-192">For more information, see [Object States and Change-Tracking](object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="82469-193">Kimlik Önbelleğinde zaten eklenen nesneyle aynı kimliğe sahip bir varlık <xref:System.Data.Linq.DuplicateKeyException> nesnesi oluşursa, bir atılmıştır.</span><span class="sxs-lookup"><span data-stu-id="82469-193">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="82469-194">Bir `IEnumerable` nesne kümesiyle iliştirdiğinizde, zaten varolan bir anahtar bulunduğunda a <xref:System.Data.Linq.DuplicateKeyException> atılır.</span><span class="sxs-lookup"><span data-stu-id="82469-194">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="82469-195">Kalan nesneler eklenmez.</span><span class="sxs-lookup"><span data-stu-id="82469-195">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82469-196">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82469-196">See also</span></span>

- [<span data-ttu-id="82469-197">LINQ to SQL ile N Katmanı ve Uzak Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="82469-197">N-Tier and Remote Applications with LINQ to SQL</span></span>](n-tier-and-remote-applications-with-linq-to-sql.md)
- [<span data-ttu-id="82469-198">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="82469-198">Background Information</span></span>](background-information.md)
