---
title: N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: 706dbda98d0e1674b76ebc6a25c7a34746720ea2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247360"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a>N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)
Müşteriler veya siparişler gibi varlık nesnelerini bir ağ üzerinden bir istemciye serileştirçalıştığınızda, bu varlıklar veri bağlamlarından ayrılır. Veri bağlamı artık yaptıkları değişiklikleri veya ilişkilerini diğer nesnelerle izlemediğinden. Bu, istemcilerin yalnızca verileri okuduğu sürece bir sorun değildir. Ayrıca, istemcilerin bir veritabanına yeni satırlar eklemesini sağlamak oldukça kolaydır. Bununla birlikte, uygulamanız, istemcilerin verileri güncelleştirebilmesini veya silmesine gerek duymalıdır, çağrı <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>yapmadan önce varlıkları yeni bir veri bağlamına iliştirmelidir. Buna ek olarak, özgün değerlerle iyimser eşzamanlılık denetimi kullanıyorsanız, veritabanını hem özgün varlık hem de varlığı değiştirilmiş olarak sağlamak için bir yol gerekir. Yöntemler `Attach` , daha sonra varlıkları kullanımdan kaldırıldıktan sonra yeni bir veri bağlamına yerleştirmeye olanak tanımak için verilmiştir.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Varlıkların yerine ara sunucu nesnelerini serileştirseniz bile, verileri veritabanına göndermek için veri erişim katmanında (dal) bir varlık oluşturmanız ve bunu yeni <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>bir ile bağlamanız gerekir.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]varlıkların serileştirilme şekli hakkında tamamen farklıdır. Windows Communication Foundation (WCF) kullanılarak seri hale getirilebilir sınıflar oluşturmak için nesne ilişkisel Tasarımcısı ve SQLMetal araçlarının nasıl kullanılacağı hakkında daha fazla bilgi için bkz [. nasıl yapılır: Varlıkları seri hale](how-to-make-entities-serializable.md)getirilebilir yapın.  
  
> [!NOTE]
> Yalnızca yeni veya `Attach` Serisi kaldırılan varlıklarda Yöntemleri çağırın. Bir varlığın özgün veri bağlamından ayrılması için tek yol, onun serileştirilmesi içindir. Ayrılmamış bir varlığı yeni bir veri bağlamına iliştirmeye çalışırsanız ve bu varlığın önceki veri bağlamından [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ertelenmiş yükleyiciler varsa, bir özel durum oluşturulur. İki farklı veri bağlamlarından ertelenmiş yükleyicileriyle bir varlık, bu varlıkta ekleme, güncelleştirme ve silme işlemlerini gerçekleştirdiğinizde istenmeyen sonuçlara neden olabilir. Ertelenmiş yükleyiciler hakkında daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).  
  
## <a name="retrieving-data"></a>Veri alma  
  
### <a name="client-method-call"></a>İstemci yöntemi çağrısı  
 Aşağıdaki örneklerde, bir Windows Forms istemcisinden DAL için örnek yöntem çağrısı gösterilmektedir. Bu örnekte, DAL bir Windows hizmet kitaplığı olarak uygulanır:  
  
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
 Aşağıdaki örnek, Orta katmanda arabirim yönteminin bir uygulamasını gösterir. Aşağıda, aklınızda iki ana işaret verilmiştir:  
  
- , <xref:System.Data.Linq.DataContext> Yöntem kapsamında bildirilmiştir.  
  
- Yöntemi, gerçek sonuçların <xref:System.Collections.IEnumerable> bir koleksiyonunu döndürür. Seri hale getirici, sonuçları istemci/sunum katmanına geri göndermek için sorguyu yürütür. Sorgu sonuçlarına yerel olarak Orta katmanda erişmek için, sorgu değişkenine veya `ToList` `ToArray` öğesini çağırarak yürütmeye zorlayabilirsiniz. Daha sonra, bu listeyi veya diziyi bir `IEnumerable`olarak döndürebilirsiniz.  
  
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
  
 Veri bağlamının bir örneği bir "iş birimi" süresine sahip olmalıdır. Gevşek olarak bağlanmış bir ortamda, bir iş birimi genellikle küçük, tek bir çağrı `SubmitChanges`dahil olmak üzere tek bir iyimser işlem olur. Bu nedenle, veri bağlamı oluşturulup Yöntem kapsamında atılmış olur. Çalışma birimi iş kuralları mantığına çağrılar içeriyorsa, genellikle `DataContext` örneği bu bütün işlem için tutmak isteyeceksiniz. Her durumda, `DataContext` örneklerin rastgele işlem sırasında uzun süreler boyunca etkin tutulması amaçlanmamıştır.  
  
 Bu yöntem, ürün nesnelerini döndürür ancak her ürünle ilişkili Order_Detail nesnelerinin koleksiyonunu değil. Bu varsayılan davranışı değiştirmek için nesnesinikullanın.<xref:System.Data.Linq.DataLoadOptions> Daha fazla bilgi için [nasıl yapılır: Ilgili verilerin ne kadar alındığını](how-to-control-how-much-related-data-is-retrieved.md)denetleyin.  
  
## <a name="inserting-data"></a>Veri ekleme  
 Yeni bir nesne eklemek için sunum katmanı yalnızca orta katman arabirimindeki ilgili yöntemi çağırır ve yeni nesnede eklenecek şekilde geçer. Bazı durumlarda, istemcinin yalnızca bazı değerleri geçmesi ve ortadaki katmanın tam nesneyi oluşturmasına daha etkili olabilir.  
  
### <a name="middle-tier-implementation"></a>Orta katman uygulama  
 Orta katmanda yeni <xref:System.Data.Linq.DataContext> bir oluşturulur, <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> nesne <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yöntemi kullanılarak <xref:System.Data.Linq.DataContext> öğesine iliştirilir ve çağrıldığında nesne eklenir. Özel durumlar, geri çağrılar ve hata koşulları diğer Web hizmeti senaryolarında olduğu gibi işlenebilirler.  
  
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
 Veritabanından varolan bir nesneyi silmek için sunum katmanı, ortadaki katman arabirimindeki ilgili yöntemi çağırır ve Silinecek nesnenin orijinal değerlerini içeren kopyasına geçirilir.  
  
 Silme işlemleri iyimser eşzamanlılık denetimleri içerir ve Silinecek nesnenin önce yeni veri bağlamına bağlanması gerekir. Bu örnekte, `Boolean` parametresi, nesnesinin zaman damgası ( `false` rowversion) olmadığını belirtmek için olarak ayarlanır. Veritabanı tablonuz her kayıt için zaman damgaları üretilemez, eşzamanlılık denetimleri özellikle istemci için çok daha basittir. Yalnızca orijinal veya değiştirilmiş nesneyi geçirin ve `Boolean` parametresini olarak `true`ayarlayın. Herhangi bir durumda, Orta katmanda genellikle yakalamak <xref:System.Data.Linq.ChangeConflictException>gerekir. İyimser eşzamanlılık çakışmalarını işleme hakkında daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](optimistic-concurrency-overview.md)bakış.  
  
 İlişkili tablolarda yabancı anahtar kısıtlamalarına sahip varlıkları silerken, önce <xref:System.Data.Linq.EntitySet%601> koleksiyonlarındaki tüm nesneleri silmeniz gerekir.  
  
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
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]iyimser eşzamanlılık içeren bu senaryolarda güncelleştirmeleri destekler:  
  
- Zaman damgaları veya RowVersion numaralarına göre iyimser eşzamanlılık.  
  
- Varlık özelliklerinin bir alt kümesinin orijinal değerlerini temel alan iyimser eşzamanlılık.  
  
- Tüm özgün ve değiştirilmiş varlıklar temelinde iyimser eşzamanlılık.  
  
 Ayrıca, bir varlıkta bir varlık üzerinde güncelleştirmeler veya silmeler, örneğin bir müşteri ve ilişkili sıralama nesnelerinin bir koleksiyonu gibi işlemleri de yapabilirsiniz. İstemcide bir varlık nesneleri ve onların alt (`EntitySet`) koleksiyonları grafiğinde değişiklikler yaptığınızda ve iyimser eşzamanlılık denetimleri orijinal değerler gerektirdiğinde, istemci her varlık için bu özgün değerleri sağlamalıdır ve <xref:System.Data.Linq.EntitySet%601> nesne. İstemcilerinin tek bir yöntem çağrısında ilgili bir dizi ilgili güncelleştirme, silme ve ekleme yapmasını etkinleştirmek istiyorsanız, istemciye her varlıkta ne tür bir işlemin gerçekleştirileceğini belirten bir yol sağlamanız gerekir. Daha sonra, kullanmadan önce her varlık <xref:System.Data.Linq.ITable.Attach%2A> için uygun yöntemi ve sonra <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>veya <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (Eklenenler <xref:System.Data.Linq.DataContext.SubmitChanges%2A>olmadan `Attach`) yöntemini çağırmanız gerekir. Güncelleştirmeleri denemeden önce özgün değerleri elde etmenin bir yolu olarak veritabanından veri alma.  
  
 İyimser eşzamanlılık hakkında daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](optimistic-concurrency-overview.md)bakış. İyimser eşzamanlılık değişikliği çakışmalarını çözme hakkında ayrıntılı bilgi için bkz [. nasıl yapılır: Değişiklik çakışmalarını](how-to-manage-change-conflicts.md)yönetin.  
  
 Aşağıdaki örneklerde her senaryo gösterilmektedir:  
  
### <a name="optimistic-concurrency-with-timestamps"></a>Zaman damgalarına sahip iyimser eşzamanlılık  
  
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
  
### <a name="with-subset-of-original-values"></a>Özgün değerlerin alt kümesiyle  
 Bu yaklaşımda istemci, tüm serileştirilmiş nesneyi, değiştirilecek değerlerle birlikte döndürür.  
  
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
  
### <a name="with-complete-entities"></a>Tüm varlıklarla  
  
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
  
 Bir koleksiyonu güncelleştirmek için <xref:System.Data.Linq.ITable.AttachAll%2A> `Attach`yerine çağırın.  
  
### <a name="expected-entity-members"></a>Beklenen varlık üyeleri  
 Daha önce belirtildiği gibi, `Attach` yöntemleri çağırmadan önce yalnızca belirli varlık nesnesi üyelerinin ayarlanması gerekir. Ayarlanması gereken varlık üyelerinin aşağıdaki kriterleri yerine getirilmesi gerekir:  
  
- Varlığın kimliğinin bir parçası olun.  
  
- Değiştirilmesi bekleniyor.  
  
- Bir zaman damgası olun veya <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özniteliği bir `Never`öğe olarak ayarlanır.  
  
 Bir tablo, iyimser eşzamanlılık denetimi için zaman damgası veya sürüm numarası kullanıyorsa, bu üyeleri çağırmadan <xref:System.Data.Linq.ITable.Attach%2A>önce ayarlamanız gerekir. Bu sütun özniteliğinde özelliği true olarak ayarlandığında, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> bir üye iyimser eşzamanlılık denetimi için ayrılmıştır. İstenen tüm güncelleştirmeler yalnızca sürüm numarası veya zaman damgası değerleri veritabanında aynı ise gönderilir.  
  
 Üye, olarak <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> `Never`ayarlı olmadığı sürece iyimser eşzamanlılık denetiminde de kullanılır. Varsayılan değer, başka `Always` bir değer belirtilmemişse olur.  
  
 Bu gerekli üyelerin herhangi biri eksikse, ("satır bulunamadı <xref:System.Data.Linq.ChangeConflictException> veya değiştirildi" <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ) sırasında bir oluşturulur.  
  
### <a name="state"></a>Durum  
 Bir varlık nesnesi <xref:System.Data.Linq.DataContext> örneğe eklendikten sonra, nesne `PossiblyModified` durumunda olduğu kabul edilir. Eklenmiş bir nesneyi kabul `Modified`etmeye zorlamak için üç yol vardır.  
  
1. Bunu değiştirilmemiş olarak ekleyin ve ardından alanları doğrudan değiştirin.  
  
2. Geçerli ve orijinal nesne örneklerini alan aşırıyüklemeyeekleyin.<xref:System.Data.Linq.Table%601.Attach%2A> Bu değişiklik izleyicisini eski ve yeni değerlerle sağlar, böylece hangi alanların değiştirildiğini otomatik olarak bilir.  
  
3. İkinci bir Boole parametresi alan aşırıyüklemeyeekleyin(trueolarakayarlanır).<xref:System.Data.Linq.Table%601.Attach%2A> Bu, değişiklik izleyicide herhangi bir özgün değer sağlamak zorunda kalmadan değiştirilen nesneyi kabul edecek şekilde söyleyecektir. Bu yaklaşımda, nesnenin bir sürüm/zaman damgası alanı olması gerekir.  
  
 Daha fazla bilgi için bkz. [nesne durumları ve değişiklik izleme](object-states-and-change-tracking.md).  
  
 Bir varlık nesnesi, iliştirilmekte olan nesneyle aynı kimliğe sahip kimlik önbelleğinde zaten gerçekleşirse, bir <xref:System.Data.Linq.DuplicateKeyException> oluşturulur.  
  
 Bir `IEnumerable` nesne kümesiyle birlikte eklediğinizde <xref:System.Data.Linq.DuplicateKeyException> , zaten varolan bir anahtar olduğunda oluşturulur. Kalan nesneler ekli değil.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL ile N Katmanı ve Uzak Uygulamalar](n-tier-and-remote-applications-with-linq-to-sql.md)
- [Arka Plan Bilgileri](background-information.md)
