---
title: İyimser Eşzamanlılık
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: ddb53c9224d56803c3528d79c5ccdf5534b9ab03
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039812"
---
# <a name="optimistic-concurrency"></a>İyimser Eşzamanlılık
Çok kullanıcılı bir ortamda, veritabanındaki verileri güncelleştirmek için iki model vardır: iyimser eşzamanlılık ve Kötümser eşzamanlılık. <xref:System.Data.DataSet> nesnesi, verilerin uzaktan iletişimini ve verilerle etkileşimde bulunmak gibi uzun süreli etkinlikler için iyimser eşzamanlılık kullanımını teşvik etmek üzere tasarlanmıştır.  
  
 Kötümser eşzamanlılık, diğer kullanıcıların verileri geçerli kullanıcıyı etkileyecek şekilde değiştirmesini engellemek için veri kaynağındaki satırları kilitlemeyi içerir. Bir kötümser modelde, bir Kullanıcı bir kilidin uygulanmasına neden olan bir eylem gerçekleştirdiğinde, diğer kullanıcılar kilit sahibi tarafından serbest gelinceye kadar kilit ile çakışacak eylemler gerçekleştiremez. Bu model öncelikle veriler için ağır çekişme olduğu ortamlarda kullanılır. böylece, kilitleri olan verileri koruma maliyetinin eşzamanlılık çakışmalarının oluşması durumunda işlem geri alma maliyetinden daha az olması sağlanır.  
  
 Bu nedenle, Kötümser eşzamanlılık modelinde bir satırı güncelleştiren bir Kullanıcı bir kilit oluşturur. Kullanıcı güncelleştirmeyi tamamlayana ve kilidi serbest bırakılana kadar, başka hiç kimse bu satırı değiştiremez. Bu nedenle, kayıt işlemleri için programlı işleme gibi kilit süreleri kısa olduğunda, Kötümser eşzamanlılık en iyi şekilde uygulanır. Kullanıcılar verilerle etkileşim kurarken ve kayıtların görece büyük süreler boyunca kilitlenmesine neden olan Kötümser eşzamanlılık, ölçeklenebilir bir seçenek değildir.  
  
> [!NOTE]
> Aynı işlemde birden çok satırı güncelleştirmeniz gerekiyorsa, bir işlem oluşturmak, kötümser kilitlemeyi kullanmaktan daha ölçeklenebilir bir seçenektir.  
  
 Buna karşılık, iyimser eşzamanlılık kullanan kullanıcılar, okurken bir satırı kilitlemez. Bir Kullanıcı bir satırı güncelleştirmek istediğinde, uygulamanın, okuduğundan bu yana başka bir kullanıcının satırı değiştirip değiştirilmediğini belirlemesi gerekir. İyimser eşzamanlılık genellikle veriler için düşük çekişme olan ortamlarda kullanılır. Kayıt kilitleme gerekli olmadığından ve kayıt kilitlemesi ek sunucu kaynakları gerektirdiğinden iyimser eşzamanlılık performansı geliştirir. Ayrıca, kayıt kilitlerini sürdürmek için veritabanı sunucusuna kalıcı bir bağlantı gerekir. Bu durum bir iyimser eşzamanlılık modelinde olduğu için sunucu bağlantıları, daha az sayıda istemciye daha az zaman sunmaya ücretsizdir.  
  
 Bir iyimser eşzamanlılık modelinde, bir kullanıcı veritabanından bir değer aldıktan sonra, ilk Kullanıcı onu değiştirmeye çalışmadan önce değeri değiştirdiğinde, bir ihlalin oluştuğu kabul edilir. Sunucu bir eşzamanlılık ihlalinin nasıl çözümlendiğine göre en iyi şekilde aşağıdaki örnek açıklanarak gösterilir.  
  
 Aşağıdaki tablolar, iyimser eşzamanlılık örneğini izler.  
  
 Kullanıcı1 1:00:00 ' da aşağıdaki değerlere sahip bir satırı veritabanından okur:  
  
 **CustId LastName adı**  
  
 101 Smith Bob  
  
|Sütun adı|Özgün değer|Geçerli değer|Veritabanındaki değer|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustId|101|101|101|  
|Soyadı|Uludağ|Uludağ|Uludağ|  
|firstName|Olduğundan|Olduğundan|Olduğundan|  
  
 Kullanıcı2, 1:01:00 ' da aynı satırı okur.  
  
 Kullanıcı2 1:03, "Bob" **iken "** Robert" olarak değiştirilir ve veritabanını günceller.  
  
|Sütun adı|Özgün değer|Geçerli değer|Veritabanındaki değer|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustId|101|101|101|  
|Soyadı|Uludağ|Uludağ|Uludağ|  
|firstName|Olduğundan|Can|Olduğundan|  
  
 Güncelleştirme sırasında veritabanındaki değerler, kullanıcı2 'nin özgün değerleriyle eşleştiği için güncelleştirme başarılı olur.  
  
 Kullanıcı1 1:05, "Bob" adının adını "James" olarak değiştirir ve satırı güncelleştirmeye çalışır.  
  
|Sütun adı|Özgün değer|Geçerli değer|Veritabanındaki değer|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustId|101|101|101|  
|Soyadı|Uludağ|Uludağ|Uludağ|  
|firstName|Olduğundan|James|Can|  
  
 Bu noktada, veritabanındaki değer ("Robert") artık Kullanıcı1 'in beklediği orijinal değerle ("emre") eşleşmediği için Kullanıcı1 bir iyimser eşzamanlılık ihlaline rastlandı. Eşzamanlılık ihlali, güncelleştirmenin başarısız olduğunu bilmenizi sağlar. Artık kararların, Kullanıcı1 tarafından sağlanan değişikliklerle ilgili olarak belirtilen değişikliklerin üzerine yazılıp yazılmayacağı veya Kullanıcı1 tarafından yapılan değişiklikleri iptal edilip edilmeyeceğini yazmanız gerekir.  
  
## <a name="testing-for-optimistic-concurrency-violations"></a>Iyimser eşzamanlılık Ihlalleri için test etme  
 İyimser eşzamanlılık ihlalinin test edilmesi için çeşitli teknikler vardır. Biri, tabloya bir zaman damgası sütunu dahil içerir. Veritabanları genellikle kaydın en son güncelleştirildiği tarih ve saati belirlemek için kullanılan zaman damgası işlevlerini sağlar. Bu tekniği kullanarak, tablo tanımına bir zaman damgası sütunu eklenir. Kayıt her güncelleştirildiğinde, zaman damgası geçerli tarih ve saati yansıtacak şekilde güncelleştirilir. İyimser eşzamanlılık ihlallerine yönelik bir testte, zaman damgası sütunu tablo içeriğinin herhangi bir sorgusuyla döndürülür. Bir güncelleştirme denendiğinde, veritabanındaki zaman damgası değeri, değiştirilen satırda yer alan özgün zaman damgası değeriyle karşılaştırılır. Eşleşiyorsa, güncelleştirme gerçekleştirilir ve zaman damgası sütunu, güncelleştirmenin yansıtılması için geçerli zaman ile güncelleştirilir. Eşleşmiyorsa, iyimser eşzamanlılık ihlali meydana geldi.  
  
 İyimser eşzamanlılık ihlalinin test edilmesine yönelik başka bir teknik de, bir satırdaki tüm özgün sütun değerlerinin veritabanında bulunan olanlarla aynı olduğunu doğrulamadır. Örneğin, aşağıdaki sorguyu göz önünde bulundurun:  
  
```sql
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 **Table1**içinde bir satırı güncelleştirirken iyimser eşzamanlılık ihlalini sınamak IÇIN aşağıdaki güncelleştirme ifadesini verirsiniz:  
  
```sql
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 Özgün değerler veritabanındaki değerlerle eşleştiği sürece, güncelleştirme gerçekleştirilir. Bir değer değiştirildiyse güncelleştirme satırı değiştirmez çünkü WHERE yan tümcesi bir eşleşme bulamaz.  
  
 Sorgunuzda her zaman benzersiz bir birincil anahtar değeri döndürülmesi önerildiğini unutmayın. Aksi halde, önceki UPDATE deyimleri birden fazla satırı güncelleştirebilir, bu, sizin amacınız olabilir.  
  
 Veri kaynağınızdaki bir sütun null değerlere izin veriyorsa, yerel tablonuzda ve veri kaynağında eşleşen bir null başvurusu denetlemek için WHERE yan tümcesini genişletmeniz gerekebilir. Örneğin, aşağıdaki UPDATE bildiriminde, yerel satırdaki null başvurusunun, veri kaynağında null başvurusuyla hala eşleştiğini veya yerel satırdaki değerin hala veri kaynağındaki değerle eşleştiğini doğrular.  
  
```sql
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 İyimser eşzamanlılık modeli kullanırken daha az kısıtlayıcı ölçütler uygulamayı da tercih edebilirsiniz. Örneğin, WHERE yan tümcesindeki birincil anahtar sütunlarının kullanılması, diğer sütunların son sorgudan bu yana güncelleştirilip güncelleştirilmediğini ne olursa olsun verilerin üzerine yazılmasına neden olur. Yalnızca belirli sütunlara bir WHERE yan tümcesi uygulayabilirsiniz ve belirli alanlar son sorgulandıktan sonra güncellenmemişse verilerin üzerine yazılmasına neden olur.  
  
### <a name="the-dataadapterrowupdated-event"></a>DataAdapter. RowUpdated olayı  
 <xref:System.Data.Common.DataAdapter> nesnesinin **RowUpdated** olayı, daha önce açıklanan tekniklerle birlikte kullanılarak iyimser eşzamanlılık ihlallerinin uygulamanıza yönelik bildirim sağlar. **RowUpdated** , bir **veri kümesinden** **değiştirilen** bir satırı güncelleştirme denemesinden sonra oluşur. Bu, bir özel durum oluştuğunda işleme, özel hata bilgileri ekleme, yeniden deneme mantığı ekleme vb. gibi özel işleme kodu eklemenizi sağlar. <xref:System.Data.Common.RowUpdatedEventArgs> nesnesi, bir tablodaki değiştirilmiş bir satır için belirli bir Update komutundan etkilenen satır sayısını içeren bir **Recordsamısson** özelliği döndürür. Güncelleştirme komutunu iyimser eşzamanlılık için test edecek şekilde ayarlayarak, **Recordsaetkilenmeyen** özelliği, bir sonuç olarak bir iyimser eşzamanlılık ihlali meydana geldiğinde 0 değerini döndürür, çünkü hiçbir kayıt güncelleştirilmemiş. Bu durumda, bir özel durum oluşturulur. **RowUpdated** olayı, bu oluşumu idare etmenizi ve **UpdateStatus. SkipCurrentRow**gibi uygun bir **RowUpdatedEventArgs. Status** değeri ayarlayarak özel durumu önlemenize olanak sağlar. **RowUpdated** olayı hakkında daha fazla bilgi için bkz. [DataAdapter olaylarını işleme](handling-dataadapter-events.md).  
  
 İsteğe bağlı olarak, **Güncelleştir**' i çağırmadan önce **DataAdapter. devam updateıse** 'yi **true**olarak ayarlayabilir ve **güncelleştirme** tamamlandığında belirli bir satırın **RowError** özelliğinde depolanan hata bilgilerine yanıt verebilirsiniz. Daha fazla bilgi için bkz. [satır hata bilgileri](./dataset-datatable-dataview/row-error-information.md).  
  
## <a name="optimistic-concurrency-example"></a>İyimser eşzamanlılık örneği  
 Aşağıda, bir **DataAdapter** 'ın **UpdateCommand** öğesini iyimser eşzamanlılık için test etmek üzere ayarlayan ve ardından iyimser eşzamanlılık Ihlallerini test etmek için **RowUpdated** olayını kullanan basit bir örnek verilmiştir. İyimser eşzamanlılık ihlaliyle karşılaşıldığında, uygulama güncelleştirmenin verildiği satırın **RowError hatasını** bir iyimser eşzamanlılık ihlalini yansıtacak şekilde ayarlar.  
  
 UPDATE komutunun WHERE yan tümcesine geçirilen parametre değerlerinin kendi sütunlarının **özgün** değerleriyle eşlendiğine unutmayın.  
  
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
