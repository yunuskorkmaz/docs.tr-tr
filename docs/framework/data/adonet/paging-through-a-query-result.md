---
title: Bir sorgu sonucunu sayfalama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 5d86095586af273f62980fcf8ddf10804b1cfa5a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514335"
---
# <a name="paging-through-a-query-result"></a>Bir sorgu sonucunu sayfalama
Bir sorgu sonucunu sayfalama bir sorgunun sonuçlarını veri sayfaları ve daha küçük alt kümelerini döndürme işlemidir. Bu, kolay yönetilmesi, küçük öbekler halinde bir kullanıcı için sonuçları görüntülemek için yaygın bir uygulamadır.  
  
 **DataAdapter** verilerine aşırı yüklemeleri yalnızca bir sayfanın döndürmek için bir olanak sağlar. **dolgu** yöntemi. Ancak, bu büyük sorgu sonuçları için disk belleği için en iyi seçim olmayabilir ancak **DataAdapter** hedef doldurur <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> yalnızca istenen kayıtları döndürmek için kaynaklar ile tüm sorgu yine de kullanılır. Tüm sorgu döndürülecek kaynakların kullanmadan bir veri kaynağından veri sayfasını döndürmek için yalnızca bu gerekli için döndürülen satırları Azalt sorgunuz için ek ölçüt belirtin.  
  
 Kullanmak için **doldurun** yöntemi, verilerin bir sayfaya dönmek için belirtin bir **startRecord** veri sayfasında ilk kayıt için bir parametre ve bir **maxRecords** sayısı parametresi kayıt sayfasında veri.  
  
 Aşağıdaki kod örneği kullanma işlemini gösterir **dolgu** sayfa boyutunu beş kayıtların bulunduğu bir sorgu sonucunun ilk sayfaya dönmek için yöntemi.  
  
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
  
 Önceki örnekte, **veri kümesi** yalnızca beş kaydeder, ancak tüm ile doldurulmuş **siparişler** tablo döndürülür. Doldurmak için **veri kümesi** aynı beş kayıtları, ancak yalnızca dönüş beş kayıt, üst kullanın ve aşağıdaki kod örneğinde olduğu gibi SQL deyiminde WHERE yan tümcelerini.  
  
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
  
 Bu şekilde sorgu sonuçları aracılığıyla disk belleği, satırları benzersiz kimliği kayıtlarının, sonraki sayfaya dönmek için aşağıdaki kod örneğinde gösterildiği gibi Command'e için siparişleri benzersiz tanımlayıcısı korumak, unutmayın.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 Sonraki aşırı yüklemesini kullanarak kayıt sayfasına dönmek için **dolgu** gereken yöntemini **startRecord** ve **maxRecords** parametreleri geçerli kayıt dizine göre artırın Sayfa boyutunu ve doldurma tablo. Veritabanı sunucusu yalnızca bir sayfa kaydı eklenir olsa bile tüm sorgu sonuçlarını döndürür unutmayın **veri kümesi**. Aşağıdaki kod örneğinde, veri sonraki sayfa ile doldurulmuş önce tablo satırları temizlenir. Belirli bir veritabanı sunucuya azaltmak için bir yerel önbellekteki döndürülen satır sayısını korumak isteyebilirsiniz.  
  
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
  
 Veritabanı sunucusu tüm sorgu zorunda kalmadan kayıtları sonraki sayfasına dönmek için SELECT deyimi kısıtlayıcı ölçütü belirtin. Yukarıdaki örnekte, döndürülen en son kaydını korunur olduğundan, WHERE yan tümcesindeki sorgu için bir başlangıç noktası belirtmek için aşağıdaki kod örneğinde gösterildiği gibi kullanabilirsiniz.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
