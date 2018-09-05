---
title: İyimser eşzamanlılık
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: 641a1cc0fd0ec53872ee3312e7da06923b82ddd7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507611"
---
# <a name="optimistic-concurrency"></a>İyimser eşzamanlılık
Çok kullanıcılı bir ortamda, bir veritabanındaki verileri güncelleştirmek için iki modeli vardır: iyimser eşzamanlılık ve kötümser eşzamanlılık. <xref:System.Data.DataSet> Nesne iyimser eşzamanlılık uzak veri ve veriler ile etkileşim kurmanın gibi uzun süre çalışan etkinlikler için kullanılmasını teşvik için tasarlanmıştır.  
  
 Kötümser eşzamanlılık, diğer kullanıcıların geçerli kullanıcıyı etkileyen bir biçimde veri değiştirmesini önlemek için veri kaynağında satırları kilitleme gerektirir. Bir kullanıcı uygulanacak kilit neden olan bir eylem gerçekleştirdiğinde kötümser modelinde, diğer kullanıcıların kilit sahibi bırakmadan, kilidiyle çakışıyor eylemi gerçekleştiremezsiniz. Bu model, öncelikle ortamlarda kullanılır bulunduğu ağır Çekişme verisi için böylece kilit ile verileri koruma maliyeti eşzamanlılık çakışma olursa işlemleri geri maliyeti'dan küçük.  
  
 Bu nedenle, bir eşzamanlılık modelinde, bir satırı güncelleştirir bir kullanıcı bir kilit oluşturur. Kullanıcı güncelleştirme tamamlandı ve kilidi serbest kadar başka hiç kimse bu satırın değiştirebilirsiniz. Kilit sürelerini kısa, kayıtları programlama işlenmesini olduğu gibi, bu nedenle, en iyi kötümser eşzamanlılık uygulanır. Kullanıcılar verilerle etkileşim ve kayıtları görece büyük sürelerle kilitlenmesine neden kötümser eşzamanlılık ölçeklenebilir bir seçenek değil.  
  
> [!NOTE]
>  Aynı işlemde birden çok satır güncelleştirmeniz gerekiyorsa, sonra da bir işlem oluşturarak kötümser kilitleme kullanmaktan daha ölçeklenebilir bir seçenektir.  
  
 Aksine, iyimser eşzamanlılık kullanan kullanıcılar bir satır, okuma sırasında kilit yok. Bir satırı güncelleştirmek bir kullanıcı istediği zaman, uygulama okunduktan sonra başka bir kullanıcı satır değişip değişmediğini belirlemeniz gerekir. İyimser eşzamanlılık genellikle düşük bir çakışma ile ortamlarda verileri için kullanılır. İyimser eşzamanlılık hiçbir kayıtları kilitleme gereklidir ve kayıtları kilitleme ek sunucu kaynakları gerekir çünkü performansını artırır. Ayrıca, kayıt kilitleri sürdürmek için veritabanı sunucusu için kalıcı bir bağlantı gereklidir. İyimser eşzamanlılık model durumda olmadığından bağlantı sunucuya daha kısa sürede çok sayıda istemcilerinin sunmak ücretsizdir.  
  
 İyimser eşzamanlılık modelinde, bir ihlali kullanıcı veritabanından bir değer aldıktan sonra ilk kullanıcının bunu değiştirmesine izin çalıştı önce başka bir kullanıcı değerini değiştirir, gerçekleşen kabul edilir. Sunucu, eşzamanlılık ihlalinin nasıl çözümler? aşağıdaki örnekte açıklayarak en iyi şekilde gösterilir.  
  
 Aşağıdaki tablolarda, iyimser eşzamanlılık örneği izleyin.  
  
 Kullanıcı1, 13: 00'da, aşağıdaki değerlerle veritabanından bir satır okur:  
  
 **CustId Soyadı adı**  
  
 101 Smith Bob  
  
|Sütun adı|Özgün değeri|Geçerli değer|Veritabanında değeri|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustId|101|101|101|  
|Soyadı|Smith|Smith|Smith|  
|FirstName|Bob|Bob|Bob|  
  
 1: 01'de, aynı satırdaki kullanıcı2 okur.  
  
 13: 03'da, kullanıcı2 değişiklikleri **FirstName** "Robert" için "Bob" dan ve veritabanını güncelleştirir.  
  
|Sütun adı|Özgün değeri|Geçerli değer|Veritabanında değeri|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustId|101|101|101|  
|Soyadı|Smith|Smith|Smith|  
|FirstName|Bob|Robert|Bob|  
  
 Veritabanı güncelleştirmesi sırasındaki değerler kullanıcı2 olan orijinal değerleri eşleştiğinden Güncelleştirme başarılı olur.  
  
 1: 05'te, User1 "James" için "Bob" ın adını değiştirir ve satırı güncelleştirmek çalışır.  
  
|Sütun adı|Özgün değeri|Geçerli değer|Veritabanında değeri|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustId|101|101|101|  
|Soyadı|Smith|Smith|Smith|  
|FirstName|Bob|James|Robert|  
  
 Bu noktada, artık User1 ("Kemal") bekliyor özgün değer ("Robert") veritabanındaki değerle eşleştiğinden User1 iyimser eşzamanlılık ihlali karşılaşır. Eşzamanlılık ihlali, yalnızca, güncelleştirmenin başarısız olduğunu bilmenizi sağlar. Kararı artık User1 tarafından sağlanan değişikliklerle kullanıcı2 tarafından sağlanan değişikliklerin üzerine ya da değişiklikleri iptal etmek için User1 tarafından yapılması gerekir.  
  
## <a name="testing-for-optimistic-concurrency-violations"></a>İyimser eşzamanlılık ihlalleri için test etme  
 İyimser eşzamanlılık ihlali için test etmek için çeşitli teknikler vardır. Bir tabloda bir zaman damgası sütunu dahil olmak üzere içerir. Veritabanları, yaygın olarak, tarih ve saat kaydın son güncelleştirildiği tanımlamak için kullanılan zaman damgası işlevler sunar. Bu tekniği kullanarak, bir zaman damgası sütunu tablosu tanımında dahil edilir. Kayıt güncelleştirildiğinde, zaman damgası geçerli tarih ve saat yansıtacak şekilde güncelleştirilir. İyimser eşzamanlılık ihlalleri için bir test çalışmasında, zaman damgası sütunu tablonun içeriğini herhangi bir sorgu ile döndürülür. Bir güncelleştirme çalışırken veritabanındaki zaman damgası değeri değiştirilmiş satırda bulunan orijinal zaman damgası değeri karşılaştırılır. Eşleşiyorlarsa güncelleştirme yapılmadan ve zaman damgası sütununu güncelleştirme yansıtacak şekilde geçerli zamanıyla güncelleştirilir. Bunlar eşleşmiyorsa, iyimser eşzamanlılık ihlali oluştu.  
  
 İyimser eşzamanlılık ihlali için test etmek için başka bir teknik bir satırdaki tüm özgün sütun değerlerini yine de veritabanında bulunanlar eşleştiğini doğrulamaktır. Örneğin, aşağıdaki sorguyu göz önünde bulundurun:  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 İyimser eşzamanlılık ihlali için bir satır güncelleştirirken test etmek için **Table1**, aşağıdaki UPDATE deyiminin sorun:  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 Orijinal değerleri veritabanındaki değerlerin aynı olduğu sürece, güncelleştirme gerçekleştirilir. Bir değer değiştirildiğinde güncelleştirme satır çünkü değiştirmeyeceğini WHERE yan tümcesi bir eşleşme bulamaz.  
  
 Her zaman sorgunuza birincil benzersiz anahtar değer döndürmek için önerilen unutmayın. Aksi takdirde, önceki güncelleştirme deyim amacınızla olmayabilir birden fazla satır güncelleştirebilir.  
  
 Veri kaynağınızı sütununda null değerlere izin veriyorsa, eşleşen bir null başvuru yerel tablonuzdaki ve veri kaynağındaki denetlemek için WHERE yan tümcesini genişletir gerekebilir. Örneğin, aşağıdaki UPDATE deyiminin bir null başvuru yerel sıradaki yine de veri kaynağında null bir başvuru eşleştiğini veya yerel satır değeri yine de veri kaynağında değerle eşleştiğinden emin doğrular.  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 İyimser eşzamanlılık modeli kullanılırken daha az kısıtlayıcı ölçütlerini uygulamak seçebilirsiniz. Örneğin, WHERE yan tümcesi verileri diğer sütunları bu yana son sorgu olup güncelleştirildi bakılmaksızın üzerine yazılmasına neden olur, yalnızca birincil anahtar sütunlarını kullanarak. WHERE yan tümcesi yalnızca belirli sütunları için belirli alanları son sorgulanan bu yana güncelleştirilen sürece üzerine yazılmasını verilerinde kaynaklanan de uygulayabilirsiniz.  
  
### <a name="the-dataadapterrowupdated-event"></a>DataAdapter.RowUpdated olay  
 **RowUpdated** olayı <xref:System.Data.Common.DataAdapter> nesne iyimser eşzamanlılık ihlallerinin uygulamanıza bildirim sağlamak için daha önce açıklanan olan tekniklerle birlikte kullanılabilir. **RowUpdated** güncelleştirmek için her girişimden sonra gerçekleşir bir **değiştirilen** gelen satır bir **veri kümesi**. Bu özel durum oluştuğunda işleme, özel hata bilgilerini ekleme, yeniden deneme mantığı ekleme dahil olmak üzere, özel işleme kodu eklemenizi ve benzeri sağlar. <xref:System.Data.Common.RowUpdatedEventArgs> Nesne döndürür bir **RecordsAffected** belirli bir güncelleştirme komut değiştirilen bir tablo satır için etkilenen satır sayısını içeren özellik. İyimser eşzamanlılık için test etmek için güncelleştirme komut ayarlayarak **RecordsAffected** özelliği sonuç olarak, döndürecektir 0 değerini iyimser eşzamanlılık ihlali oluştu, hiç kayıt güncelleştirilmediğinden. Bu durumda, bir özel durum oluşturulur. **RowUpdated** olay sağlar, bu durum işlemek ve uygun bir ayarlayarak özel durumdan kaçınmak **RowUpdatedEventArgs.Status** gibi değerini  **UpdateStatus.SkipCurrentRow**. Hakkında daha fazla bilgi için **RowUpdated** olay bkz [DataAdapter olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
 İsteğe bağlı olarak ayarlayabileceğiniz **DataAdapter.ContinueUpdateOnError** için **true**, çağırmadan önce **güncelleştirme**ve içindedepolananhatabilgileriniyanıtlar**RowError** özelliği belirli bir satır **güncelleştirme** tamamlandı. Daha fazla bilgi için [satır hatası bilgileri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).  
  
## <a name="optimistic-concurrency-example"></a>İyimser eşzamanlılık örneği  
 Aşağıdaki ayarlar basit bir örnektir **UpdateCommand** , bir **DataAdapter** iyimser eşzamanlılık için test etmek ve ardından **RowUpdated** sınamak için olay İyimser eşzamanlılık ihlalleri. İyimser eşzamanlılık ihlali ile karşılaşıldığında, uygulamanın ayarlar **RowError** güncelleştirme iyimser eşzamanlılık ihlali yansıtacak şekilde için verilmiş satır.  
  
 Güncelleştir komutunun WHERE yan tümcesi için geçirilen parametre değerlerini eşlendiğine dikkat edin **özgün** karşılık gelen sütun değerleri de.  
  
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
Dim parameter As SqlParameter = dataSet.UpdateCommand.Parameters.Add( _  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Satır Hatası Bilgileri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 [İşlemler ve Eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
