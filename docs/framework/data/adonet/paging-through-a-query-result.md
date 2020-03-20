---
title: Sorgu Sonucunu Sayfalama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 2e7fb97e5c0cb42deff43c411f47e8d30e2257ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149394"
---
# <a name="paging-through-a-query-result"></a>Sorgu Sonucunu Sayfalama
Sorgu sonucunu gözden geçirmek, sorgu sonuçlarını daha küçük veri alt kümelerinde veya sayfalarda döndürme işlemidir. Bu, sonuçları küçük, kolay yönetilen parçalar halinde kullanıcıya görüntülemek için yaygın bir uygulamadır.  
  
 **DataAdapter,** **Dolgu** yönteminin aşırı yükleri yoluyla yalnızca bir sayfa veriyi döndürmek için bir tesis sağlar. Ancak, **DataAdapter** hedefi <xref:System.Data.DataTable> doldursa veya <xref:System.Data.DataSet> yalnızca istenen kayıtlarla doldursa da, tüm sorguyu döndürecek kaynaklar hala kullanıldığından, bu büyük sorgu sonuçları arasında gezinmek için en iyi seçenek olmayabilir. Sorgunun tamamını döndürmek için kaynakları kullanmadan bir veri kaynağından veri sayfası döndürmek için, sorgunuz için yalnızca gerekli olansatırları azaltan ek ölçütler belirtin.  
  
 Bir veri sayfasını döndürmek için **Dolgu** yöntemini kullanmak için, veri sayfasındaki ilk kayıt için **bir başlangıç Kaydı** parametresi ve veri sayfasındaki kayıt sayısı için bir **maxRecords** parametresi belirtin.  
  
 Aşağıdaki kod örneği, sayfa boyutunun beş kayıt olduğu bir sorgu sonucunun ilk sayfasını döndürmek için **Dolgu** yönteminin nasıl kullanılacağını gösterir.  
  
```vb  
Dim currentIndex As Integer = 0  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT * FROM dbo.Orders ORDER BY OrderID"  
' Assumes that connection is a valid SqlConnection object.  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
int currentIndex = 0;  
int pageSize = 5;  
  
string orderSQL = "SELECT * FROM Orders ORDER BY OrderID";  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 Önceki örnekte, **DataSet** yalnızca beş kayıtla doldurulur, ancak **Siparişler** tablosunun tamamı döndürülür. **DataSet'i** aynı beş kayıtla doldurmak, ancak yalnızca beş kayıt döndürmek için, aşağıdaki kod örneğinde olduğu gibi SQL ekstrenizdeki TOP ve WHERE yan tümcelerini kullanın.  
  
```vb  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT TOP " & pageSize & _  
  " * FROM Orders ORDER BY OrderID"  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Orders")
```  
  
```csharp  
int pageSize = 5;  
  
string orderSQL = "SELECT TOP " + pageSize +
  " * FROM Orders ORDER BY OrderID";  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Orders");  
```  
  
 Sorgu sonuçları arasında bu şekilde gezinirken, aşağıdaki kod örneğinde gösterildiği gibi, benzersiz kimliği komuta geçirmek için satırları sıralayan benzersiz tanımlayıcıyı korumanız gerektiğini unutmayın.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 **StartRecord** ve **maxRecords** parametrelerini alan **Dolgu** yönteminin aşırı yükünü kullanarak kayıtların bir sonraki sayfasını döndürmek için, geçerli kayıt dizini sayfa boyutuna göre artım ve tabloyu doldurun. **DataSet'e**yalnızca bir sayfa kayıt eklense bile veritabanı sunucusunun tüm sorgu sonuçlarını döndürtettiğini unutmayın. Aşağıdaki kod örneğinde, tablo satırları bir sonraki veri sayfasıyla doldurulmadan önce temizlenir. Veritabanı sunucusuna yapılan gezileri azaltmak için yerel bir önbellekte belirli sayıda döndürülen satırı korumak isteyebilirsiniz.  
  
```vb  
currentIndex = currentIndex + pageSize  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
currentIndex += pageSize;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 Veritabanı sunucusunun sorgunun tamamını döndürmesine gerek kalmadan kayıtların bir sonraki sayfasını döndürmek için, kısıtlayıcı ölçütleri SELECT deyimine belirtin. Önceki örnek döndürülen son kaydı koruduğundan, aşağıdaki kod örneğinde gösterildiği gibi sorgu için bir başlangıç noktası belirtmek için WHERE yan tümcesinde kullanabilirsiniz.  
  
```vb  
orderSQL = "SELECT TOP " & pageSize & _  
  " * FROM Orders WHERE OrderID > " & lastRecord & " ORDER BY OrderID"  
adapter.SelectCommand.CommandText = orderSQL  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, "Orders")  
```  
  
```csharp  
orderSQL = "SELECT TOP " + pageSize +
  " * FROM Orders WHERE OrderID > " + lastRecord + " ORDER BY OrderID";  
adapter.SelectCommand.CommandText = orderSQL;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, "Orders");  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
