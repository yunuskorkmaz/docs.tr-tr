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
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a>N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)
Bir ağ üzerinden bir istemci müşteriler veya siparişler gibi varlık nesnelerini seri hale getirmek, bu varlıklar, veri bağlamından ayrılır. Veri bağlamı artık değişikliklerini veya diğer nesnelerle ilişkilerini izler. İstemcileri yalnızca verileri okumasını sürece, bir sorun değildir. İstemcilerin bir yeni satır eklemek oldukça kolaydır. İstemcileri güncelleştirin veya veri silemezsiniz uygulamanız gerekiyorsa çağırmadan önce ancak ardından varlıkları için yeni bir veri bağlamı eklediğiniz gerekir <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>. Özgün değerleriyle bir iyimser eşzamanlılık kontrolü kullanıyorsanız, ayrıca, ardından da veritabanı orijinal varlık hem varlık değiştirilmiş olarak sağlamak için bir yol almanız gerekir. `Attach` Yöntemleri ayrılmış eklendikten sonra yeni bir veri bağlamına varlıkları put olanak sağlanır.  
  
 Proxy nesneleri yerine seri hale getirme bile [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varlıkları devam veri erişim katmanı (DAL) üzerinde bir varlık oluşturun ve yeni bir ekleme <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>veritabanı veri göndermek için.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varlıkları nasıl serileştirilir hakkında tamamen farklı olur. Windows Communication Foundation (WCF) kullanarak seri hale getirilebilir sınıflar oluşturmak için Nesne İlişkisel Tasarımcısı ve SQLMetal araçlarını kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Varlıkları serileştirilebilir yapmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).  
  
> [!NOTE]
>  Yalnızca çağrı `Attach` yöntemleri yeni veya seri durumdan çıkarılmış varlık. Tek bir varlığın özgün veri bağlamından ayrılacak serileştirilmesi için yoludur. Undetached bir varlık eklemek için yeni bir veri bağlamı denerseniz ve bu varlığa yine de önceki kendi veri bağlamından yükleyicileri ertelenmiş [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir özel durum olacaktır. INSERT, update ve bu varlık üzerinde silme işlemleri gerçekleştirdiğinizde iki farklı veri bağlamları gelen ertelenmiş yükleyici sahip bir varlık istenmeyen sonuçlara neden olabilir. Ertelenmiş Yükleyici hakkında daha fazla bilgi için bkz: [Ertelenen hemen yükleme](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="retrieving-data"></a>Veri alma  
  
### <a name="client-method-call"></a>İstemci yöntem çağrısı  
 Aşağıdaki örnekler, DAL bir Windows Forms istemciden bir örnek yöntem çağrısını gösterir. Bu örnekte, bir Windows hizmet kitaplığı DAL uygulanır:  
  
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
  
### <a name="middle-tier-implementation"></a>Orta katman uygulama  
 Aşağıdaki örnek, Orta katmanda arabirim yöntemini bir uygulamasını gösterir. Unutmayın, iki ana noktaları şunlardır:  
  
- <xref:System.Data.Linq.DataContext> Yöntemi kapsamda bildirilir.  
  
- Yöntem döndürür bir <xref:System.Collections.IEnumerable> gerçek sonuçlar koleksiyonu. Seri hale getirici sonuçları istemci/sunu katmanı geri gönderilecek sorgu yürütülür. Sorgu sonuçları orta katman üzerinde yerel olarak erişmek için yürütme çağırarak zorlayabilirsiniz `ToList` veya `ToArray` sorgu değişkeni üzerinde. Bu listeyi döndürür veya olarak dizi bir `IEnumerable`.  
  
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
  
 Bir veri bağlamı örneğini bir "iş birimidir." ömrünü olmalıdır Bir iş birimi zamanı gevşek bağlanmış bir ortamda, genellikle küçük, tek bir çağrı dahil olmak üzere belki de bir iyimser işlem `SubmitChanges`. Bu nedenle, veri bağlamı oluşturulur ve yöntemi kapsamında atıldı. İş kuralları mantığı çağrıları iş birimini içeren sonra genellikle tutmak isteyeceksiniz `DataContext` tüm bu işlem için örneği. Her iki durumda da `DataContext` örnekleri amaçlanmayan uzun süreler için rastgele sayıda işlem Canlı tutulması.  
  
 Bu yöntem, ürün nesneler ancak değil her ürünle ilişkilendirilmiş Order_Detail nesneleri koleksiyonunu döndürür. Kullanım <xref:System.Data.Linq.DataLoadOptions> bu varsayılan davranışı değiştirmek için nesne. Daha fazla bilgi için [nasıl yapılır: Ne kadar ilgili verilerin alındığını denetleme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).  
  
## <a name="inserting-data"></a>Veri ekleme  
 Yeni bir nesne eklemek için sunu katmanı yalnızca orta katman arabirimde ilgili yöntemi çağırır ve eklemek için yeni nesne geçirir. Bazı durumlarda, istemcinin tam nesneyi oluşturmak orta katman vardır ve yalnızca bazı değerleri geçirmek için daha verimli olabilir.  
  
### <a name="middle-tier-implementation"></a>Orta katman uygulama  
 Orta katmanda, yeni bir <xref:System.Data.Linq.DataContext> olan oluşturulan nesne bağlı <xref:System.Data.Linq.DataContext> kullanarak <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> yöntemi ve nesnenin ne zaman eklenir <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağrılır. Yalnızca tüm diğer Web hizmeti senaryosunda olduğu gibi özel durumlar, geri çağrılar ve hata koşullarını işlenebilir.  
  
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
  
## <a name="deleting-data"></a>Verileri silme  
 Var olan bir nesne veritabanından silmek için sunu katmanı orta katman arabiriminde ilgili yöntemi çağırır ve Silinecek nesnenin orijinal değerleri içeren kendi kopya geçirir.  
  
 Silme işlemi, iyimser eşzamanlılık denetimlerinin içerir ve silinecek nesne yeni veri bağlamı için önce bağlı olması gerekir. Bu örnekte, `Boolean` parametrenin ayarlanmış `false` nesne bir zaman damgası (RowVersion) sahip olmadığını göstermek için. Veritabanı tablonuzun her kayıt için zaman damgaları oluşturursanız, bu eşzamanlılık denetimlerinin özellikle istemci için kadar kolay. Yalnızca ya da özgün ya da değiştirilmiş nesnesi içinde geçirin ve ayarlama `Boolean` parametresi `true`. Herhangi bir durumda, Orta katmanda genellikle yakalamak gerekli olduğu <xref:System.Data.Linq.ChangeConflictException>. İyimser eşzamanlılık çakışmalarını işleme hakkında daha fazla bilgi için bkz. [iyimser eşzamanlılık: Genel Bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 İlişkili tablolardaki yabancı anahtar kısıtlamaları olan varlıkları silmek, tüm nesneleri önce silmeniz gerekir, <xref:System.Data.Linq.EntitySet%601> koleksiyonları.  
  
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
  
## <a name="updating-data"></a>Verileri güncelleştirme  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] İyimser eşzamanlılık içeren bu senaryolarda güncelleştirmeleri destekler:  
  
- Zaman damgaları veya sayıları göre iyimser eşzamanlılık.  
  
- Varlık özelliklerinin bir alt özgün değerlerine göre iyimser eşzamanlılık.  
  
- İyimser eşzamanlılık tam özgün ve düzeltilmiş varlıkları temel alınarak.  
  
 Bir varlıkta kendi ilişkileri, örneğin bir müşteri ve ilişkili nesnelerini sipariş koleksiyonunu birlikte, güncelleştirme ve silme gerçekleştirebilirsiniz. Yaptığınızda değişiklikler istemcide bir grafiğini varlık nesneleri ve onların alt (`EntitySet`) koleksiyonları ve iyimser eşzamanlılık denetimlerini orijinal değerleri gerektirir, istemci her varlık için özgün bu değerler sağlamanız gerekir ve <xref:System.Data.Linq.EntitySet%601> nesne. Tek bir yöntem çağrısında bir dizi ilgili güncelleştirmeler, siler ve eklemeler istemcilerin etkinleştirmek istiyorsanız, istemci her varlık üzerinde gerçekleştirilecek işlem türüne göstermek için bir yol sağlamalıdır. Orta katmanda, ardından uygun çağırmalısınız <xref:System.Data.Linq.ITable.Attach%2A> yöntemi ardından <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, veya <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (olmadan `Attach`, eklemeleri için) çağırmadan önce her varlık için <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Veritabanından bir şekilde güncelleştirmeleri denemeden önce özgün değerlerini almak için veri yok.  
  
 İyimser eşzamanlılık hakkında daha fazla bilgi için bkz: [iyimser eşzamanlılık: Genel Bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md). İyimser eşzamanlılık çözme konusunda ayrıntılı bilgi için çakışmaları değiştirmek [nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
 Aşağıdaki örnekler, her bir senaryo gösterilmektedir:  
  
### <a name="optimistic-concurrency-with-timestamps"></a>Zaman damgası ile iyimser eşzamanlılık  
  
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
  
### <a name="with-subset-of-original-values"></a>Orijinal değerleri alt kümesi ile  
 Bu yaklaşımda, istemci değiştirilmesi için değerleri ile birlikte tam serileştirilmiş nesne döndürür.  
  
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
  
### <a name="with-complete-entities"></a>Tam varlıklarla  
  
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
  
 Bir koleksiyonu güncellemek için çağrı <xref:System.Data.Linq.ITable.AttachAll%2A> yerine `Attach`.  
  
### <a name="expected-entity-members"></a>Beklenen varlık üyeleri  
 Daha önce belirtildiği gibi varlık nesnesi yalnızca belirli üyeleri çağırmadan önce ayarlamak için gerekli olan `Attach` yöntemleri. Ayarlanması gereken varlık üyeleri aşağıdaki ölçütleri karşılamalıdır:  
  
- Varlığın kimliğinin bir parçası olun.  
  
- Değiştirilecek beklenebilir.  
  
- Bir zaman damgası olmalısınız veya kendi <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özniteliği ayarlanmış yanı sıra bir şey `Never`.  
  
 Bir tablo için bir iyimser eşzamanlılık denetimi bir zaman damgası veya sürüm numarası kullanıyorsa, çağırmadan önce bu üyeler ayarlamalısınız <xref:System.Data.Linq.ITable.Attach%2A>. Bir üye için iyimser eşzamanlılık denetimi zaman adanmış <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özelliği bu sütun özniteliği true. Yalnızca sürüm numarası veya zaman damgası değerleri aynıysa veritabanında, istenen güncelleştirmeleri gönderilir.  
  
 Üyesi olmadığı sürece üyesi de iyimser eşzamanlılık kontrolü içinde kullanılan <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> kümesine `Never`. Varsayılan değer `Always` başka bir değer belirtilirse.  
  
 Bunlardan herhangi birini üyeleri eksikse, gerekirse bir <xref:System.Data.Linq.ChangeConflictException> sırasında oluşturulan <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("satır bulunamadı veya değiştirilen").  
  
### <a name="state"></a>Durum  
 Nesne sonra bir varlığa bağlı olduğu <xref:System.Data.Linq.DataContext> nesne örneği, kabul olması `PossiblyModified` durumu. Bağlı nesneyi kabul zorlamak için üç yol vardır `Modified`.  
  
1. Değiştirilmemiş olarak ekleme ve doğrudan alanları değiştirin.  
  
2. Kendisiyle ekleme <xref:System.Data.Linq.Table%601.Attach%2A> geçerli ve özgün nesne örneklerini alan aşırı yüklemesini. Değiştirilen alanları otomatik olarak bilir, böylece bu eski ve yeni değerlerle değişikliği İzleyicisi sağlar.  
  
3. Kendisiyle ekleme <xref:System.Data.Linq.Table%601.Attach%2A> ikinci (true olarak ayarlanırsa) Boolean parametresini alan aşırı yükleme. Bu, herhangi bir özgün değeri sağlamak zorunda kalmadan değiştirilmiş nesne dikkate alınması gereken değişiklik İzleyici bildirir. Bu yaklaşımda, nesnenin sürümü/zaman damgası alanı olması gerekir.  
  
 Daha fazla bilgi için [nesne durumları ve değişiklik izleme](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).  
  
 Kimliği önbelleğinde iliştirilmekte, nesne olarak aynı kimliğe sahip bir varlık nesnesine oluşursa bir <xref:System.Data.Linq.DuplicateKeyException> oluşturulur.  
  
 İle bağladığınızda bir `IEnumerable` nesneler bir <xref:System.Data.Linq.DuplicateKeyException> zaten var olan bir anahtar olmadığı durumlarda oluşturulur. Kalan nesneler bağlı değilsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
