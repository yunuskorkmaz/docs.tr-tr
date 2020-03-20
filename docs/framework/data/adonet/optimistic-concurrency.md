---
title: İyimser Eşzamanlılık
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: e8d24a3998ca97fdf45e647bc40c1f7d6018ec20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149459"
---
# <a name="optimistic-concurrency"></a>İyimser Eşzamanlılık
Çok kullanıcılı bir ortamda, veritabanındaki verileri güncelleştirmek için iki model vardır: iyimser eşzamanlılık ve kötümser eşzamanlılık. Nesne, <xref:System.Data.DataSet> verileri remoting ve verilerle etkileşim gibi uzun süren etkinlikler için iyimser eşzamanlılık kullanımını teşvik etmek üzere tasarlanmıştır.  
  
 Kötümser eşzamanlılık, diğer kullanıcıların verileri geçerli kullanıcıyı etkileyecek şekilde değiştirmesini önlemek için veri kaynağındaki satırları kilitlemeyi içerir. Kötümser bir modelde, bir kullanıcı kilidin uygulanmasına neden olan bir eylem gerçekleştirdiğinde, diğer kullanıcılar kilit sahibi onu serbest bırakana kadar kilitle çakışacak eylemleri gerçekleştiremez. Bu model, öncelikle veriler için ağır çekişmelerin olduğu ortamlarda kullanılır, böylece eşzamanlılık çakışmaları meydana geldiğinde verileri kilitlerle koruma nın maliyeti hareketleri geri alma maliyetinden daha az olur.  
  
 Bu nedenle, kötümser bir eşzamanlılık modelinde, bir satırı güncelleyen bir kullanıcı kilit oluşturur. Kullanıcı güncelleştirmeyi bitirip kilidi yayımlayana kadar, başka hiç kimse bu satırı değiştiremez. Bu nedenle, kötümser eşzamanlılık en iyi kilit süreleri kısa olacak, kayıtların programlı işleme olarak uygulanır. Kötümser eşzamanlılık, kullanıcılar verilerle etkileşimde yken ve kayıtların nispeten büyük bir süre için kilitlenmelerine neden olduğunda ölçeklenebilir bir seçenek değildir.  
  
> [!NOTE]
> Aynı işlemde birden çok satırı güncelleştirmeniz gerekiyorsa, işlem oluşturmak kötümser kilitleme kullanmaktan daha ölçeklenebilir bir seçenektir.  
  
 Bunun aksine, iyimser eşzamanlılık kullanan kullanıcılar okurken bir satırı kilitlemez. Bir kullanıcı bir satırı güncelleştirmek istediğinde, uygulamanın okunduğundan beri başka bir kullanıcının satırı değiştirip değiştirmediğini belirlemesi gerekir. İyimser eşzamanlılık genellikle veri için düşük çekişmeli ortamlarda kullanılır. İyimser eşzamanlılık, kayıtların kilitlenmesi gerekmedığından ve kayıtların kilitlemesi ek sunucu kaynakları gerektirdiğinden performansı artırır. Ayrıca, kayıt kilitlerini korumak için veritabanı sunucusuna kalıcı bir bağlantı gereklidir. İyimser bir eşzamanlılık modelinde durum böyle olmadığından, sunucuya bağlantılar daha kısa sürede daha fazla sayıda istemciye hizmet vermekte serbesttir.  
  
 İyimser bir eşzamanlılık modelinde, bir kullanıcı veritabanından bir değer aldıktan sonra, ilk kullanıcı onu değiştirmeye çalıştıönce değeri değiştirirse, bir ihlal meydana gelmiş olarak kabul edilir. Sunucunun eşzamanlılık ihlalini nasıl çözeceği en iyi şekilde ilk olarak aşağıdaki örnek açıklanır.  
  
 Aşağıdaki tablolar iyimser eşzamanlılık bir örnek izleyin.  
  
 Saat 13:00'te User1 veritabanından aşağıdaki değerlerle bir satır okur:  
  
 **CustID Soyadı Ad soyad**  
  
 101 Smith Bob  
  
|Sütun adı|Orijinal değer|Geçerli değer|Veritabanındaki değer|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|Bob|Bob|  
  
 Saat 13:01'de User2 aynı satırı okur.  
  
 Saat 13:03'te **User2, FirstName'i** "Bob"dan "Robert" olarak değiştirir ve veritabanını güncelleştirir.  
  
|Sütun adı|Orijinal değer|Geçerli değer|Veritabanındaki değer|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|Robert|Bob|  
  
 Güncelleştirme sırasında veritabanındaki değerler User2'nin sahip olduğu özgün değerlerle eşleştirdiği için güncelleştirme başarılı oldu.  
  
 Saat 13:05'te User1, "Bob"un ilk adını "James" olarak değiştirir ve satırı güncelleştirmeye çalışır.  
  
|Sütun adı|Orijinal değer|Geçerli değer|Veritabanındaki değer|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|James|Robert|  
  
 Bu noktada, Kullanıcı1 iyimser bir eşzamanlılık ihlaliyle karşılaşır, çünkü veritabanındaki değer ("Robert") artık User1'in beklediği orijinal değerle ("Bob") eşleşemez. Eşzamanlılık ihlali yalnızca güncelleştirmenin başarısız olduğunu bilmenizi sağlar. Kullanıcı1 tarafından sağlanan değişikliklerle User2 tarafından sağlanan değişikliklerin üzerine yazımının veya Kullanıcı1 tarafından yapılan değişikliklerin iptal edilmesine karar verilmesi gerekiyor.  
  
## <a name="testing-for-optimistic-concurrency-violations"></a>İyimser Eşzamanlılık İhlalleri Için Test  
 İyimser bir eşzamanlılık ihlali için test etmek için çeşitli teknikler vardır. Bir tabloda bir zaman damgası sütun dahil içerir. Veritabanları genellikle kaydın en son güncelleştirildiğinde tarih ve saati tanımlamak için kullanılabilecek zaman damgası işlevselliği sağlar. Bu teknik kullanılarak, tablo tanımına bir zaman damgası sütunu eklenmiştir. Kayıt güncelleştirildiğinde, zaman damgası geçerli tarih ve saati yansıtacak şekilde güncelleştirilir. İyimser eşzamanlılık ihlalleri için yapılan bir testte, zaman damgası sütunu tablonun içeriğinin sorgusuyla birlikte döndürülür. Bir güncelleştirme denendiğinde, veritabanındaki zaman damgası değeri değiştirilen satırda bulunan özgün zaman damgası değeriyle karşılaştırılır. Eşleşirlerse, güncelleştirme gerçekleştirilir ve zaman damgası sütunu güncelleştirmeyi yansıtacak geçerli saatle güncelleştirilir. Eşleşmezlerse, iyimser bir eşzamanlılık ihlali meydana geldi.  
  
 İyimser bir eşzamanlılık ihlalini test etmek için başka bir teknik, bir satırdaki tüm özgün sütun değerlerinin hala veritabanında bulunanlarla eşleşindiğini doğrulamaktır. Örneğin, aşağıdaki sorguyu göz önüne alın:  
  
```sql
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 **Tablo1'deki**bir satırı güncellerken iyimser bir eşzamanlılık ihlalini test etmek için aşağıdaki UPDATE deyimini yayınlayayım:  
  
```sql
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 Özgün değerler veritabanındaki değerlerle eşleşince güncelleştirme gerçekleştirilir. Bir değer değiştirildiyse, WHERE yan tümcesi eşleşme bulmayacağı için güncelleştirme satırı değiştirmez.  
  
 Sorgunuzda her zaman benzersiz bir birincil anahtar değeri döndürmeniz in tavsiye edilir. Aksi takdirde, önceki UPDATE deyimi birden fazla satırı güncelleyebilir ve bu da amacınız olmayabilir.  
  
 Veri kaynağınızdaki bir sütun nulls'a izin veriyorsa, yerel tablonuzda ve veri kaynağınızda eşleşen bir null başvurusu denetlemek için WHERE yan tümcenizi genişletmeniz gerekebilir. Örneğin, aşağıdaki UPDATE deyimi, yerel satırdaki null bir başvurunun hala veri kaynağındaki null başvurusuyla eşleştiğini veya yerel satırdaki değerin veri kaynağındaki değerle eşleşmesini doğrular.  
  
```sql
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 Ayrıca, iyimser bir eşzamanlılık modeli kullanırken daha az kısıtlayıcı ölçütuygulamayı da seçebilirsiniz. Örneğin, WHERE yan tümcesi'ndeki yalnızca birincil anahtar sütunlarını kullanmak, diğer sütunların son sorgudan beri güncelleştirilip güncelleştirilmediğine bakılmaksızın verilerin üzerine yazılmasına neden olur. Ayrıca, belirli alanlar son sorgulandıktan sonra güncelleştirilmedikçe verilerin üzerine yazılmasıyla sonuçlanan bir WHERE yan tümcesi yalnızca belirli sütunlara da uygulayabilirsiniz.  
  
### <a name="the-dataadapterrowupdated-event"></a>DataAdapter.RowUpdated Olay  
 Nesnenin <xref:System.Data.Common.DataAdapter> **RowUpdated** olayı, iyimser eşzamanlılık ihlalleri uygulamanıza bildirim sağlamak için daha önce açıklanan tekniklerle birlikte kullanılabilir. **RowUpdate,** **Bir DataSet'ten** **Değiştirilen** satırı güncelleştirmeye yönelik her denemeden sonra oluşur. Bu, özel hata bilgileri ekleme, yeniden deneme mantığı ekleme ve benzeri özel hata bilgileri ekleme gibi özel işleme kodu eklemenize olanak tanır. Nesne, <xref:System.Data.Common.RowUpdatedEventArgs> tablodaki değiştirilmiş bir satır için belirli bir güncelleştirme komutundan etkilenen satır sayısını içeren **RecordsAffected** özelliğini döndürür. İyimser eşzamanlılık için güncelleştirme komutunu ayarlayarak, **RecordsAffected** özelliği, sonuç olarak, iyimser bir eşzamanlılık ihlali oluştuğunda, hiçbir kayıt güncelleştirildiğinden 0 değerini döndürecektir. Bu durumda, bir özel durum atılır. **RowUpdate** olayı, **updatestatus.SkipCurrentRow**gibi uygun bir **RowUpdateEventArgs.Status** değeri ayarlayarak bu oluşumu işlemek ve özel durum önlemek sağlar. **RowUpdated** olayı hakkında daha fazla bilgi için [DataAdapter Olaylarını işleme](handling-dataadapter-events.md)konusuna bakın.  
  
 İsteğe bağlı olarak, Update'i aramadan önce **DataAdapter.ContinueUpdateOnError'ı** **doğru**olarak ayarlayabilir ve **Güncelleştirme**tamamlandığında **Update** belirli bir satırın **RowError** özelliğinde depolanan hata bilgilerine yanıt verebilirsiniz. Daha fazla bilgi için [Satır Hata Bilgileri'ne](./dataset-datatable-dataview/row-error-information.md)bakın.  
  
## <a name="optimistic-concurrency-example"></a>İyimser Eşzamanlılık Örneği  
 Aşağıda, bir **DataAdapter'ın** **UpdateCommand'ını** iyimser eşzamanlılık için test etmek üzere ayarlayan ve daha sonra iyimser eşzamanlılık ihlallerini sınamak için **RowUpdate** olayını kullanan basit bir örnek verilmiştir. İyimser bir eşzamanlılık ihlaliyle karşılaşıldığında, uygulama güncelleştirmenin iyimser bir eşzamanlılık ihlalini yansıtacak şekilde verildiği satırın **Satır Hatasını** ayarlar.  
  
 UPDATE komutunun WHERE yan tümcesine geçirilen parametre değerlerinin ilgili sütunlarının **Özgün** değerlerine eşlendiğine dikkat edin.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName", connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
- [Veri Kaynaklarını DataAdapters ile Güncelleştirme](updating-data-sources-with-dataadapters.md)
- [Satır Hatası Bilgileri](./dataset-datatable-dataview/row-error-information.md)
- [İşlemler ve Eşzamanlılık](transactions-and-concurrency.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
