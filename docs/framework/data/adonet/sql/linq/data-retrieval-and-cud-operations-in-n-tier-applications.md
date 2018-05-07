---
title: Veri alma ve CUD işlemleri N katmanlı uygulamalarda (LINQ-SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: ea27d6406ed588f2046dc938f5167a6c0200329e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a>Veri alma ve CUD işlemleri N katmanlı uygulamalarda (LINQ-SQL)
Bir ağ üzerinden bir istemciye müşteriler veya siparişler gibi varlık nesnesi seri hale olduğunda bu varlıkların kendi veri bağlamından ayrılır. Veri bağlamı artık kendi değişiklikler veya diğer nesnelerle ilişkilendirmelerinin izler. İstemcileri yalnızca verileri okuma sürece, bir sorun değildir. Bunu ayrıca bir yeni satırları eklemek istemcileri etkinleştirmek oldukça basittir. Uygulamanızı istemcileri güncelleştirin veya verilerini silmek mümkün gerektiriyorsa, çağırmadan önce ancak, daha sonra varlıklar için yeni bir veri bağlamı eklemeniz gerekir <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>. Özgün değerleriyle iyimser eşzamanlılık kontrolü kullanıyorsanız, ek olarak, ardından da veritabanını orijinal varlık ve varlık değiştirilmiş olarak sağlamak için bir yol gerekir. `Attach` Yöntemleri ayrılmış eklendikten sonra yeni bir veri bağlamına varlıklar put olanak sağlanır.  
  
 Yerine proxy nesneleri seri hale getirme olsa bile [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varlıkları devam veri erişim katmanı'nı (DAL) üzerinde bir varlık oluşturun ve yeni bir eklemek <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>veritabanı veri göndermek için.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varlıkları nasıl serileştirilir hakkında tamamen ilgisiz olur. Nasıl kullanılacağı hakkında daha fazla bilgi için [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ve Windows Communication Foundation (WCF) kullanarak serileştirilebilir sınıflar oluşturmak için SQLMetal araçları görmek [nasıl yapılır: varlıklar serileştirilebilir olun](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).  
  
> [!NOTE]
>  Yalnızca arama `Attach` yeni veya seri durumdan çıkarılmış varlık yöntemleri. Yalnızca kendi özgün veri bağlamından ayrılmış olması bir varlık için seri hale getirilebilmesi için yoludur. Yeni bir veri bağlamı undetached bir varlık eklemek denerseniz ve varlık önceki kendi veri bağlamından yükleyicilerini ertelenmiş [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir özel durum olacaktır. INSERT, update ve bu varlıkta silme işlemleri gerçekleştirdiğinizde iki farklı veri bağlamları gelen ertelenmiş yükleyicilerini sahip bir varlık istenmeyen sonuçlara neden olabilir. Ertelenmiş yükleyicilerini hakkında daha fazla bilgi için bkz: [hemen yüklenirken karşı ertelenmiş](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="retrieving-data"></a>Veri alma  
  
### <a name="client-method-call"></a>İstemci yöntem çağrısı  
 Aşağıdaki örnekler bir örnek yöntem çağrısı DAL için bir Windows Forms istemciden gösterir. Bu örnekte, bir Windows hizmet kitaplığı DAL uygulanır:  
  
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
 Aşağıdaki örnek arabirimi yöntemin bir uygulaması, Orta katmanda gösterir. Not etmek için iki ana noktalar şunlardır:  
  
-   <xref:System.Data.Linq.DataContext> Yöntemi kapsamda bildirilir.  
  
-   Yöntem bir <xref:System.Collections.IEnumerable> gerçek sonuçları koleksiyonu. Seri hale getirici sonuçları geri istemci/sunu katmanı göndermek için sorgu yürütülür. Sorgu sonuçları orta katman yerel olarak erişmek için yürütme çağırarak zorlayabilirsiniz `ToList` veya `ToArray` sorgu değişkeni üzerinde. Bu liste dönün veya olarak dizi bir `IEnumerable`.  
  
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
  
 Bir veri bağlamı örneğini bir "iş birimidir." ömrü olmalıdır Gevşek bağlanmış bir ortamda, bir iş birimine genellikle küçük, tek bir çağrı dahil olmak üzere belki de bir iyimser hareket `SubmitChanges`. Bu nedenle, veri bağlamı oluşturulur ve yöntemi kapsamda atıldı. İş kuralları mantığı çağrıları iş birimini içeren sonra genellikle tutmak isteyeceksiniz `DataContext` tüm bu işlem için örneği. Her iki durumda da `DataContext` örnekleri amaçlanmayan uzun süreler için işlemleri rastgele sayılar arasında Canlı tutulmalıdır.  
  
 Bu yöntem ürün nesneler ancak değil her ürünüyle ilişkilendirilen Order_Detail nesneler koleksiyonunu döndürür. Kullanım <xref:System.Data.Linq.DataLoadOptions> bu varsayılan davranışı değiştirmek için nesne. Daha fazla bilgi için bkz: [nasıl yapılır: denetim nasıl çok ilgili veriler alınır](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).  
  
## <a name="inserting-data"></a>Veri ekleme  
 Yeni bir nesne eklemek için sunu katmanı yalnızca orta katman arabirimde ilgili yöntemini çağırır ve eklemek için yeni nesne geçirir. Bazı durumlarda, tam nesne oluşturmak orta katman yalnızca bazı değerleri geçirmek ve istemci için daha etkili olabilir.  
  
### <a name="middle-tier-implementation"></a>Orta katman uygulama  
 Orta katman yeni bir <xref:System.Data.Linq.DataContext> olan oluşturulan nesneyi bağlı <xref:System.Data.Linq.DataContext> kullanarak <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> yöntemi ve nesne zaman eklenir <xref:System.Data.Linq.DataContext.SubmitChanges%2A> olarak adlandırılır. Özel durumlar, geri çağrılar ve hata koşulları yalnızca herhangi diğer Web Hizmetleri senaryosu olduğu gibi işlenebilir.  
  
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
 Varolan bir nesne veritabanından silmek için sunu katmanı orta katman arabirimde ilgili yöntemini çağırır ve Silinecek nesnenin orijinal değerleri içerir, kopyada geçirir.  
  
 Silme işlemleri iyimser eşzamanlılık denetimleri içerir ve Silinecek nesnenin yeni veri bağlamı için öncelikle bağlı olması gerekir. Bu örnekte, `Boolean` parametrenin ayarlanmış `false` nesne zaman damgası (RowVersion) sahip olup olmadığını belirtmek için. Veritabanı tablonuza damgaları her kayıt için oluşturursanız, bu eşzamanlılık denetimleri özellikle istemci için daha kolay. Yalnızca ya da özgün ya da değiştirilmiş nesne geçirmek ve ayarlamak `Boolean` parametresi `true`. Her iki durumda da Orta katmanda yakalamak genellikle ise gerekli <xref:System.Data.Linq.ChangeConflictException>. İyimser eşzamanlılık çakışmalarına hakkında daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 İlişkili tabloları yabancı anahtar kısıtlamaları olan varlıkları silmek, tüm nesneleri silmeniz gerekir, <xref:System.Data.Linq.EntitySet%601> koleksiyonları.  
  
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
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] güncelleştirmeleri iyimser eşzamanlılık içeren bu senaryolarda destekler:  
  
-   İyimser eşzamanlılık zaman damgaları veya RowVersion numaraları bağlı.  
  
-   İyimser eşzamanlılık varlık özelliklerinin bir alt özgün değerlerine göre.  
  
-   İyimser eşzamanlılık üzerinde tam özgün ve değiştirilen varlıklar tabanlı.  
  
 Örneğin bir müşteri ve ilişkili sipariş nesnelerini koleksiyonu kendi ilişkileri ile birlikte bir varlıkta güncelleştirme veya silme de gerçekleştirebilirsiniz. Yaptığınızda değişiklikleri istemcide varlık nesneler ve onların alt grafiğe (`EntitySet`) koleksiyonlar ve iyimser eşzamanlılık denetimleri gerektiren özgün değerler, her bir varlık için istemci bu özgün değerler sağlamanız gerekir ve <xref:System.Data.Linq.EntitySet%601> nesne. İstemcilerin bir dizi ilgili güncelleştirmeler, siler ve eklemeleri tek yöntemi çağırmaya izin vermek istiyorsanız, istemci her varlık üzerinde gerçekleştirilecek işlem türünü belirtmek için bir yol sağlamalısınız. Orta katmanda, ardından uygun çağırmalısınız <xref:System.Data.Linq.ITable.Attach%2A> yöntemi ve ardından <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, veya <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (olmadan `Attach`, eklemeleri için) çağırmadan önce her bir varlık için <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Veritabanından güncelleştirmeleri denemeden önce özgün değerler elde etmenin bir yolu verileri değil.  
  
 İyimser eşzamanlılık hakkında daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md). Değiştirme çakışmaları iyimser eşzamanlılık çözme konusunda ayrıntılı bilgi için bkz: [nasıl yapılır: değiştirme çakışmaları yönetmek](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
 Aşağıdaki örnekler, her bir senaryo gösterilmektedir:  
  
### <a name="optimistic-concurrency-with-timestamps"></a>Zaman damgalı iyimser eşzamanlılık  
  
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
  
### <a name="with-subset-of-original-values"></a>Özgün değerleri alt kümesiyle  
 Bu yaklaşımda, istemci değerlerin değiştirilmesi birlikte tam serileştirilmiş nesne döndürür.  
  
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
  
### <a name="with-complete-entities"></a>Tam varlıklarıyla  
  
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
 Daha önce belirtildiği gibi yalnızca varlık nesnesi belirli üyeleri çağırmadan önce ayarlamak için gerekli olan `Attach` yöntemleri. Ayarlanması gereken varlık üyeleri aşağıdaki ölçütleri yerine getirmeniz gerekir:  
  
-   Varlığın kimliğini bir parçası olarak.  
  
-   Değiştirilecek beklenen.  
  
-   Bir zaman damgası olmalısınız veya kendi <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özniteliği kümesine yanı sıra bir şey `Never`.  
  
 Bir tablo iyimser eşzamanlılık kontrolü için bir zaman damgası veya sürüm numarasını kullanıyorsa, arama yapmadan önce bu üyeler ayarlamalısınız <xref:System.Data.Linq.ITable.Attach%2A>. Üyesi olduğunda denetimi iyimser eşzamanlılık ayrılmış <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özelliği ayarlanmış bu sütun özniteliği true. Yalnızca sürüm numarasını veya zaman damgası değerlerini veritabanında aynıysa istenen güncelleştirmeleri gönderilir.  
  
 Üye sahip olmadığı sürece üyesi de iyimser eşzamanlılık kontrolü kullanılan <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> kümesine `Never`. Varsayılan değer `Always` başka bir değer belirtilmişse.  
  
 Bunlardan herhangi bir üye eksik, gerekirse bir <xref:System.Data.Linq.ChangeConflictException> sırasında oluşturulan <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("satır bulunamadı veya değiştirilen").  
  
### <a name="state"></a>Durum  
 Sonra bir varlık nesnesini bağlı <xref:System.Data.Linq.DataContext> örneği, nesne olarak kabul olması `PossiblyModified` durumu. Kabul edilmesi için iliştirilmiş bir nesne zorlamak için üç yolla `Modified`.  
  
1.  Değiştirilmemiş olarak ekleyin ve doğrudan alanları değiştirin.  
  
2.  İle ekleme <xref:System.Data.Linq.Table%601.Attach%2A> aşırı geçerli ve özgün nesne örneklerini alır. Bu otomatik olarak hangi alanların değişmiş bilmesini bu eski ve yeni değerlerle değişikliği İzleyicisi sağlar.  
  
3.  İle ekleme <xref:System.Data.Linq.Table%601.Attach%2A> ikinci Boolean parametresini (true olarak ayarlanmış) alan aşırı. Bu, tüm özgün değerler sağlamak zorunda kalmadan değiştirilmiş nesne dikkate alınması gereken değişikliği İzleyicisi söyler. Bu yaklaşımda, nesnenin sürümü/zaman damgası alanı olması gerekir.  
  
 Daha fazla bilgi için bkz: [nesne durumlarını ve değişiklik izleme](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).  
  
 Kimliği önbelleğinde iliştirilmekte, nesne aynı kimliğe sahip bir varlık nesnesine oluşursa bir <xref:System.Data.Linq.DuplicateKeyException> oluşturulur.  
  
 Ne zaman attach ile birlikte bir `IEnumerable` bir nesne, bir <xref:System.Data.Linq.DuplicateKeyException> zaten mevcut bir anahtarı mevcut olduğunda oluşturulur. Kalan nesneler eklenmemiş.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
