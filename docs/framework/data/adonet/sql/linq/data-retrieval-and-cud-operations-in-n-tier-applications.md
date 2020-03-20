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
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a>N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)
Müşteri veya Siparişler gibi varlık nesnelerini bir ağ üzerinden istemciye serihale ettiğinizde, bu varlıklar veri bağlamından ayrılır. Veri bağlamı artık değişikliklerini veya diğer nesnelerle ilişkilendirmelerini izletmez. İstemciler yalnızca verileri okuduğu sürece bu bir sorun değildir. İstemcilerin veritabanına yeni satırlar eklemesini sağlamak da nispeten basittir. Ancak, uygulamanız istemcilerin verileri güncelleştirebilmelerini veya silebilmelerini gerektiriyorsa, aramadan <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>önce varlıkları yeni bir veri bağlamına iliştirmeniz gerekir. Buna ek olarak, özgün değerlerle iyimser bir eşzamanlılık denetimi kullanıyorsanız, veritabanını hem özgün varlığı hem de varlığı değiştirilmiş olarak sağlamanın bir yolunu da emegerekir. Yöntemler, `Attach` varlıkları ayrıldıktan sonra yeni bir veri bağlamına koymanızı sağlamak için sağlanır.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Varlıkların yerine proxy nesnelerini seri hale getirmeniz olsa bile, verileri veritabanına göndermek için veri erişim katmanında <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>(DAL) bir varlık oluşturmanız ve yeni bir ,'ye eklemeniz gerekir.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]varlıkların nasıl seri hale getirilen hakkında tamamen kayıtsız. Windows Communication Foundation (WCF) kullanarak serileştirilebilir sınıflar oluşturmak için Object İlişkisel Tasarımcı ve SQLMetal araçlarının nasıl kullanılacağı hakkında daha fazla bilgi için [bkz.](how-to-make-entities-serializable.md)  
  
> [!NOTE]
> Yalnızca yeni `Attach` veya deserialized varlıklar üzerindeki yöntemleri arayın. Bir varlığın özgün veri bağlamından ayrılmasının tek yolu seri hale getirilmesidir. Yeni bir veri bağlamına ayrılmamış bir varlık eklemeye çalışırsanız ve bu varlık hala [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] önceki veri bağlamından ertelenmiş yükleyicileri varsa, bir özel durum atacaktır. İki farklı veri bağlamından ertelenmiş yükleyicilere sahip bir varlık, bu varlıktaki ekleme, güncelleştirme ve silme işlemlerini gerçekleştirdiğiniz zaman istenmeyen sonuçlara neden olabilir. Ertelenmiş yükleyiciler hakkında daha fazla bilgi için [Ertelenmiş ve Hemen Yükleme](deferred-versus-immediate-loading.md)bölümüne bakın.  
  
## <a name="retrieving-data"></a>Veri Alma  
  
### <a name="client-method-call"></a>İstemci Yöntemi Çağrısı  
 Aşağıdaki örnekler, bir Windows Forms istemcisinden DAL'ye örnek bir yöntem çağrısı gösterir. Bu örnekte, DAL Bir Windows Hizmet Kitaplığı olarak uygulanır:  
  
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
  
### <a name="middle-tier-implementation"></a>Orta Katman Uygulaması  
 Aşağıdaki örnekte, arabirim yönteminin orta katmanda bir uygulaması gösterilmektedir. Dikkat edilmesi gereken iki ana nokta şunlardır:  
  
- Yöntem <xref:System.Data.Linq.DataContext> kapsamında bildirilir.  
  
- Yöntem, gerçek <xref:System.Collections.IEnumerable> sonuçların bir koleksiyonunu döndürür. Serileştirici, sonuçları istemci/sunu katmanına geri göndermek için sorguyu yürütecektir. Sorgu sonuçlarına orta katmandaki yerel olarak erişmek için, `ToList` `ToArray` sorgu değişkenini arayarak veya sorgu değişkenini kullanarak yürütmeyi zorlayabilirsiniz. Daha sonra bu listeyi veya `IEnumerable`diziyi bir .  
  
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
  
 Bir veri bağlamı örneğinin bir "çalışma birimi" ömrü olmalıdır. Gevşek bir leştiği ortamda, bir iş birimi genellikle küçük, belki de tek bir çağrı `SubmitChanges`da dahil olmak üzere iyimser bir işlem. Bu nedenle, veri bağlamı oluşturulur ve yöntem kapsamında atılır. Çalışma birimi iş kuralları mantığına çağrılar içeriyorsa, genellikle `DataContext` bu tüm işlem için örnek tutmak isteyeceksiniz. Her durumda, `DataContext` örneklerin rasgele sayıda hareket arasında uzun süre canlı tutulması amaçlanmamıştır.  
  
 Bu yöntem, Ürün nesnelerini döndürecek, ancak her Ürünle ilişkili Order_Detail nesnelerin inkisini döndürmez. Bu <xref:System.Data.Linq.DataLoadOptions> varsayılan davranışı değiştirmek için nesneyi kullanın. Daha fazla bilgi için bkz: İlgili Verilerin Ne Kadar ını [Denetle.](how-to-control-how-much-related-data-is-retrieved.md)  
  
## <a name="inserting-data"></a>Veri ekleme  
 Yeni bir nesne eklemek için sunu katmanı yalnızca orta katman arabiriminde ilgili yöntemi çağırır ve eklemek için yeni nesnegeçer. Bazı durumlarda, istemcinin yalnızca bazı değerleri geçirmesi ve orta katmanın tam nesneyi oluşturmasını sağlamak daha verimli olabilir.  
  
### <a name="middle-tier-implementation"></a>Orta Katman Uygulaması  
 Orta katmanda, yeni <xref:System.Data.Linq.DataContext> bir oluşturulur, nesne <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> yöntem kullanılarak eklenir ve çağrıldığında <xref:System.Data.Linq.DataContext.SubmitChanges%2A> nesne eklenir. Özel durumlar, geri aramalar ve hata koşulları, diğer Web hizmeti senaryolarında olduğu gibi işlenebilir.  
  
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
  
## <a name="deleting-data"></a>Veri silme  
 Varolan bir nesneyi veritabanından silmek için, sunu katmanı orta katman arabirimindeki ilgili yöntemi çağırır ve silinecek nesnenin özgün değerlerini içeren kopyasına geçer.  
  
 Silme işlemleri iyimser eşzamanlılık denetimleri içerir ve silinecek nesnenin önce yeni veri bağlamına eklenmesi gerekir. Bu örnekte, `Boolean` parametre nesnenin bir zaman damgası (RowVersion) olmadığını belirtmek için `false` ayarlanır. Veritabanı tablonuz her kayıt için zaman damgaları oluşturuyorsa, eşzamanlılık denetimleri özellikle istemci için çok daha basittir. Orijinal veya değiştirilmiş nesneyi geçirin `Boolean` ve parametreyi 'ye `true`ayarlayın Her durumda, orta katmanda genellikle yakalamak için <xref:System.Data.Linq.ChangeConflictException>gereklidir. İyimser eşzamanlılık çakışmaları hakkında daha fazla bilgi için [Bkz. İyimser Eşzamanlılık: Genel Bakış.](optimistic-concurrency-overview.md)  
  
 İlişkili tablolarda yabancı anahtar kısıtlamaları olan varlıkları silerken, önce <xref:System.Data.Linq.EntitySet%601> koleksiyonlarındaki tüm nesneleri silmeniz gerekir.  
  
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
  
## <a name="updating-data"></a>Verileri Güncelleme  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]iyimser eşzamanlılık içeren bu senaryolarda güncelleştirmeleri destekler:  
  
- Zaman damgaları veya RowVersion numaralarına dayalı iyimser eşzamanlılık.  
  
- Varlık özellikleri alt kümesinin özgün değerlerine dayalı iyimser eşzamanlılık.  
  
- Orijinal ve değiştirilmiş varlıkların tamamına dayalı iyimser eşzamanlılık.  
  
 Müşteri ve ilişkili Sipariş nesnelerinin bir koleksiyonu gibi, bir varlık üzerindeki güncelleştirmeleri veya silmeleri ilişkileriyle birlikte de gerçekleştirebilirsiniz. Varlık nesneleri ve alt ( )`EntitySet`koleksiyonlarının grafiğinde istemci üzerinde değişiklikler yaptığınızda ve iyimser eşzamanlılık denetimleri özgün değerler gerektiriyorsa, istemci her varlık ve <xref:System.Data.Linq.EntitySet%601> nesne için bu özgün değerleri sağlamalıdır. İstemcilerin tek bir yöntem çağrısında ilgili güncelleştirmeler, silmeler ve eklemeler kümesi yapmasını sağlamak istiyorsanız, istemciye her varlıkta ne tür bir işlem gerçekleştireceklerini belirtmek için bir yol sağlamanız gerekir. Orta katmanda, daha sonra, <xref:System.Data.Linq.ITable.Attach%2A> aramadan <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>önce <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>her <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> varlık `Attach`için uygun yöntemi aramanız ve <xref:System.Data.Linq.DataContext.SubmitChanges%2A>ardından , veya (eklemeler için olmadan) aramanız gerekir. Güncelleştirmeleri denemeden önce özgün değerleri elde etmek için veritabanından veri almayın.  
  
 İyimser eşzamanlılık hakkında daha fazla bilgi için, [Bkz. İyimser Eşzamanlılık: Genel Bakış.](optimistic-concurrency-overview.md) İyimser eşzamanlılık değişikliği çakışmalarını çözme hakkında ayrıntılı bilgi için [bkz.](how-to-manage-change-conflicts.md)  
  
 Aşağıdaki örnekler her senaryoyu gösterir:  
  
### <a name="optimistic-concurrency-with-timestamps"></a>Zaman damgaları ile iyimser eşzamanlılık  
  
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
  
### <a name="with-subset-of-original-values"></a>Orijinal Değerlerin Alt Kümesi ile  
 Bu yaklaşımda, istemci değiştirilecek değerlerle birlikte serileştirilmiş nesnenin tamamını döndürür.  
  
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
  
### <a name="with-complete-entities"></a>Komple Varlıklarla  
  
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
  
 Koleksiyonu güncelleştirmek için, `Attach`"' yerine çağırın. <xref:System.Data.Linq.ITable.AttachAll%2A>  
  
### <a name="expected-entity-members"></a>Beklenen Varlık Üyeleri  
 Daha önce belirtildiği gibi, `Attach` yöntemleri çağırmadan önce yalnızca belirli varlık nesnesinin üyelerinin ayarlatılması gerekir. Ayarlanılması gereken varlık üyeleri aşağıdaki ölçütleri karşılamalıdır:  
  
- Varlığın kimliğinin bir parçası olun.  
  
- Değiştirilmesi bekleniyor.  
  
- Bir zaman damgası <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> olun veya özniteliği `Never`yanında bir şey ayarlanmış olması.  
  
 Bir tablo iyimser bir eşzamanlılık denetimi için bir zaman damgası veya sürüm <xref:System.Data.Linq.ITable.Attach%2A>numarası kullanıyorsa, bu üyeleri aramadan önce ayarlamanız gerekir. Bir üye, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> özellik bu Sütun özniteliği üzerinde doğru ayarlandığında iyimser eşzamanlılık denetimi için adamıştır. İstenen güncelleştirmeler yalnızca sürüm numarası veya zaman damgası değerleri veritabanında aynıysa gönderilir.  
  
 Bir üye, iyimser eşzamanlılık denetiminde de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> `Never`kullanılır. Varsayılan değer, `Always` başka bir değer belirtilmemişse değerdir.  
  
 Bu gerekli üyelerden herhangi biri <xref:System.Data.Linq.ChangeConflictException> eksikse, bir satır ("Satır bulunamadı veya değiştirilmez") sırasında <xref:System.Data.Linq.DataContext.SubmitChanges%2A> atılır.  
  
### <a name="state"></a>Durum  
 Bir varlık nesnesi <xref:System.Data.Linq.DataContext> örneğe iliştirildikten sonra, nesne `PossiblyModified` durumda olarak kabul edilir. Ekli bir nesneyi dikkate `Modified`almaya zorlamanın üç yolu vardır.  
  
1. Değiştirilmemiş olarak takın ve sonra alanları doğrudan değiştirin.  
  
2. Geçerli ve <xref:System.Data.Linq.Table%601.Attach%2A> özgün nesne örneklerini alan aşırı yükletin. Bu, hangi alanların değiştiğini otomatik olarak bilecek şekilde değişim izleyicisini eski ve yeni değerlerle birlikte sağlar.  
  
3. İkinci bir <xref:System.Data.Linq.Table%601.Attach%2A> Boolean parametresi (doğru ayarlanmış) alır aşırı yük ile takın. Bu, değişiklik izleyicisine, özgün değerler sağlamak zorunda kalmadan nesneyi değiştirildiğini düşünmesini söyler. Bu yaklaşımda, nesnenin bir sürüm/zaman damgası alanı olmalıdır.  
  
 Daha fazla bilgi için [bkz.](object-states-and-change-tracking.md)  
  
 Kimlik Önbelleğinde zaten eklenen nesneyle aynı kimliğe sahip bir varlık <xref:System.Data.Linq.DuplicateKeyException> nesnesi oluşursa, bir atılmıştır.  
  
 Bir `IEnumerable` nesne kümesiyle iliştirdiğinizde, zaten varolan bir anahtar bulunduğunda a <xref:System.Data.Linq.DuplicateKeyException> atılır. Kalan nesneler eklenmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](n-tier-and-remote-applications-with-linq-to-sql.md)
- [Arka Plan Bilgileri](background-information.md)
