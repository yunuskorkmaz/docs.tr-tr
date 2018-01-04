---
title: "İyimser eşzamanlılık"
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
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0cd77b63c54b926c21641024c7688476cef2fdcf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="optimistic-concurrency"></a>İyimser eşzamanlılık
Çok kullanıcılı bir ortamda bir veritabanındaki verileri güncelleştirmek için iki model vardır: iyimser eşzamanlılık ve eşzamanlılık. <xref:System.Data.DataSet> Nesne remoting veri ve veri ile etkileşim gibi uzun süre çalışan etkinlikleri için iyimser eşzamanlılık kullanımını teşvik şekilde tasarlanmıştır.  
  
 Eşzamanlılık satırları diğer kullanıcıların verileri geçerli kullanıcının etkileyen şekilde değiştirmesini engellemek için veri kaynağında kilitleme içerir. Bir kullanıcı uygulanması için bir kilit neden olan bir eylem gerçekleştirir kötümser modelinde, diğer kullanıcıların kilit sahibi bırakması kadar kilidiyle çakışabilir işlemleri gerçekleştirilemez. Bu model, öncelikle ortamlarda kullanılır söz konusu olduğunda, veriler için yoğun Çekişme böylece kilitleri ile verileri koruma maliyeti eşzamanlılık çakışma meydana gelirse işlemleri geri maliyetini'dan küçük.  
  
 Bu nedenle, bir eşzamanlılık modelde kilit bir satır güncelleştirmeleri bir kullanıcı oluşturur. Kullanıcı güncelleştirme tamamlandı ve kilidi serbest kadar hiç kimsenin satır değiştirebilirsiniz. Kilit kez kısa, kayıtları programlı işlenmesini olduğu gibi, bu nedenle, en iyi eşzamanlılık uygulanır. Kullanıcılar veri ile etkileşim ve kayıtları görece büyük süreyle kilitlenmesine neden eşzamanlılık ölçeklenebilir bir seçenek değil.  
  
> [!NOTE]
>  Aynı işlemde birden çok satır güncellemeniz gerekiyorsa, bir işlem oluşturma kötümser kilitleme kullanmaktan daha ölçeklenebilir bir seçenektir.  
  
 Bunun aksine, iyimser eşzamanlılık kullanan kullanıcılar bir satır onu okunurken kilit yok. Bir kullanıcı bir satırı güncelleştirme istediğinde, uygulamayı başka bir kullanıcı bunu okunuşundan bu yana satır değişip değişmediğini belirlemeniz gerekir. İyimser eşzamanlılık genellikle düşük bir çakışma ile ortamlarda veriler için kullanılır. İyimser eşzamanlılık hiçbir kayıtları kilitleme gereklidir ve kayıtları kilitleme ek sunucu kaynakları gerekir çünkü performansı artırır. Ayrıca, kayıt kilitleri korumak için veritabanı sunucusu kalıcı bir bağlantı gereklidir. İyimser eşzamanlılık modeli durumda olmadığından sunucusuna bağlantılarda daha kısa sürede çok sayıda istemciler hizmet ücretsizdir.  
  
 İyimser eşzamanlılık modelinde, bir ihlali kullanıcı veritabanından bir değer aldıktan sonra ilk kullanıcı bunu değiştirmeye çalıştı önce başka bir kullanıcı değeri değiştirirse, oluşmuş kabul edilir. Sunucu bir eşzamanlılık ihlali nasıl çözümlediği aşağıdaki örnekte açıklayarak en iyi şekilde gösterilir.  
  
 Aşağıdaki tablolarda iyimser eşzamanlılık örneği izleyin.  
  
 1: 00'da, Kullanıcı1 veritabanı aşağıdaki değerlere sahip bir satır okur:  
  
 **CustId Soyadı adı**  
  
 101 Smith Bob  
  
|Sütun adı|Özgün değeri|Geçerli değer|Veritabanında değeri|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustId|101|101|101|  
|Soyadı|Smith|Smith|Smith|  
|FirstName|Bob|Bob|Bob|  
  
 1: 01'de, aynı satır kullanıcı2 okur.  
  
 Kullanıcı2: 03 p.M'de, 1 değiştirir **FirstName** "Robert" için "Bob" den ve veritabanını güncelleştirir.  
  
|Sütun adı|Özgün değeri|Geçerli değer|Veritabanında değeri|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustId|101|101|101|  
|Soyadı|Smith|Smith|Smith|  
|FirstName|Bob|Robert|Bob|  
  
 Güncelleştirme zaman veritabanındaki değerleri kullanıcı2 sahip özgün değerler eşleştiğinden Güncelleştirme başarılı olur.  
  
 1: p.M'de 05, Kullanıcı1 "Bob" ın adını "Can" değiştirir ve satır güncelleştirmeyi dener.  
  
|Sütun adı|Özgün değeri|Geçerli değer|Veritabanında değeri|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustId|101|101|101|  
|Soyadı|Smith|Smith|Smith|  
|FirstName|Bob|Ahmet|Robert|  
  
 Bu noktada, Kullanıcı1 ("Kemal") bekliyordu özgün değeri ("Robert") veritabanındaki değerle artık eşleştiğinden Kullanıcı1 iyimser eşzamanlılık ihlali karşılaşır. Eşzamanlılık ihlali basitçe, güncelleştirmenin başarısız olduğunu bilmenizi sağlar. Karar şimdi mi, yoksa Kullanıcı1 tarafından sağlanan değişikliklerle kullanıcı2 tarafından sağlanan değişikliklerin üzerine yazmak için değişiklikleri iptal etmek için Kullanıcı1 tarafından yapılması gerekir.  
  
## <a name="testing-for-optimistic-concurrency-violations"></a>İyimser eşzamanlılık ihlali test etme  
 İyimser eşzamanlılık ihlali için test etmek için birçok tekniği vardır. Bir tabloda bir zaman damgası sütunu dahil olmak üzere içerir. Veritabanları, genellikle kayıt en son güncelleştirildiği saat ve tarihi tanımlamak için kullanılan zaman damgası işlevsellik sağlar. Bu teknik kullanılarak, bir zaman damgası sütunu tablo tanımı dahil edilir. Kayıt güncelleştirildiğinde, zaman damgası geçerli tarih ve saat yansıtacak şekilde güncelleştirilir. İyimser eşzamanlılık ihlalleri için bir test, zaman damgası sütunu tablonun içeriği herhangi bir sorgu ile döndürülür. Bir güncelleştirme çalışırken zaman damgası değerini veritabanında değişiklik satır içinde yer alan ilk zaman damgası değeri karşılaştırılır. Eşleşirlerse, güncelleştirme gerçekleştirilir ve zaman damgası sütunu geçerli zamanla güncelleştirmesini yansıtacak şekilde güncelleştirilir. Bunlar eşleşmiyorsa iyimser eşzamanlılık ihlali oluştu.  
  
 İyimser eşzamanlılık ihlali için test etmek için başka bir teknik bir satır tüm özgün sütun değerleri hala veritabanında bulunan eşleştiğinden doğrulamaktır. Örneğin, aşağıdaki sorguyu göz önünde bulundurun:  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 İyimser eşzamanlılık ihlali için bir satır güncelleştirirken test etmek için **tablo1**, aşağıdaki güncelleştirme deyimini vermek:  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 Veritabanındaki değerleri özgün değerler eşleştiği sürece güncelleştirme gerçekleştirilir. Bir değer değiştirilirse güncelleştirme satır olduğundan değiştirmez WHERE yan tümcesi bir eşleşme bulamaz.  
  
 Her zaman sorgunuzda benzersiz bir birincil anahtar değeri döndürmek için önerilen unutmayın. Aksi takdirde, önceki güncelleştirme bildirimini maksadınızı olmayabilir birden fazla satır güncelleştirebilir.  
  
 Veri kaynağı bir sütunu null değerlere izin veriyorsa, eşleşen bir null başvuru yerel tablonuz ve veri kaynağında denetlemek için WHERE yan tümcesinde uzatma gerekebilir. Örneğin, aşağıdaki güncelleştirme deyimini yerel satırda null bir başvuru hala bir null başvuru veri kaynağında eşleşiyor veya yerel satır değeri hala veri kaynağı değerinde eşleştiğini doğrular.  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 İyimser eşzamanlılık modeli kullanılırken daha az kısıtlayıcı bir ölçüt uygulamak seçebilirsiniz. Örneğin, WHERE yan tümcesi verilerin diğer sütunların itibaren son sorgu olup güncelleştirildi bağımsız olarak üzerine yazılmasına neden olur, yalnızca birincil anahtar sütunlarını kullanarak. WHERE yan tümcesi yalnızca belirli sütunlar için en son sorgulanan bu yana belirli alanları güncelleştirilmiş sürece üzerine yazmaya verilerde kaynaklanan de uygulayabilirsiniz.  
  
### <a name="the-dataadapterrowupdated-event"></a>DataAdapter.RowUpdated olayı  
 **RowUpdated** olayı <xref:System.Data.Common.DataAdapter> nesne iyimser eşzamanlılık ihlallerinin uygulamanıza bildirim sağlamak için daha önce açıklanan teknikleri ile birlikte kullanılabilir. **RowUpdated** güncelleştirmek için her girişiminden sonra gerçekleşir bir **değiştirilen** öğesinden satır bir **DataSet**. Bu özel durum oluştuğunda işleme, özel hata bilgilerini ekleme, yeniden deneme mantığı ekleme de dahil olmak üzere özel işleme kodu eklemenizi ve benzeri sağlar. <xref:System.Data.Common.RowUpdatedEventArgs> Nesnesi döndürür bir **RecordsAffected** bir tablodaki değiştirilmiş bir satır için belirli bir güncelleştirme komutu tarafından etkilenen satırların sayısını içeren özellik. İyimser eşzamanlılık için test etmek için güncelleştirme komutu ayarlayarak **RecordsAffected** özelliği sonuç olarak, döndürecektir 0 değeri iyimser eşzamanlılık ihlali oluştu, hiçbir kayıt güncelleştirilmediğinden. Bu durumda, bir özel durum oluşur. **RowUpdated** olay sağlar, bu oluşumu işlemek ve uygun bir ayarlayarak özel durumu önlemek **RowUpdatedEventArgs.Status** gibi değerini  **UpdateStatus.SkipCurrentRow**. Hakkında daha fazla bilgi için **RowUpdated** olayı bkz [olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
 İsteğe bağlı olarak, ayarlayabileceğiniz **DataAdapter.ContinueUpdateOnError** için **true**, çağırmadan önce **güncelleştirme**ve depolananhatabilgileriniyanıtlar**RowError** belirli bir özellik satır **güncelleştirme** tamamlandı. Daha fazla bilgi için bkz: [satır hata bilgilerini](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).  
  
## <a name="optimistic-concurrency-example"></a>İyimser eşzamanlılık örneği  
 Aşağıdaki ayarlar basit bir örnektir **UpdateCommand** , bir **DataAdapter** iyimser eşzamanlılık için test etmek ve ardından **RowUpdated** sınamak için olay İyimser eşzamanlılık ihlali. İyimser eşzamanlılık ihlali karşılaşıldığında, uygulama ayarlar **RowError** güncelleştirme iyimser eşzamanlılık ihlali yansıtacak şekilde için verilmiş satır.  
  
 GÜNCELLEŞTİRME komutu WHERE yan tümcesi geçirilen parametre değerlerini eşlendiği Not **özgün** ilgili sütun değerleri de.  
  
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
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName, connection);  
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
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
