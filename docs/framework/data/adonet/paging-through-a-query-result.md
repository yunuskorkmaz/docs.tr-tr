---
description: 'Hakkında daha fazla bilgi edinin: bir sorgu sonucu Ile sayfalama'
title: Sorgu Sonucunu Sayfalama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: ead2c74e19cfb81c83c7bf1e73b0c0d7a0a7cc67
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672367"
---
# <a name="paging-through-a-query-result"></a>Sorgu Sonucunu Sayfalama

Sorgu sonucu ile sayfalama, bir sorgunun sonuçlarını, verilerin veya sayfaların küçük alt kümelerine döndürme işlemidir. Bu, sonuçları küçük ve kolay Yönetilecek öbeklerde bir kullanıcıya görüntülemek için yaygın bir uygulamadır.  
  
 **DataAdapter** , **Fill** yönteminin aşırı yüklemeleri aracılığıyla yalnızca bir veri sayfası döndürmek için bir özellik sağlar. Ancak, bu, büyük sorgu sonuçlarıyla sayfalama için en iyi seçim olmayabilir, çünkü **DataAdapter** hedefi ya da yalnızca istenen kayıtlarla doldurmakla birlikte, <xref:System.Data.DataTable> <xref:System.Data.DataSet> Tüm sorguyu döndürecek kaynaklar hala kullanılmaktadır. Tüm sorguyu döndürmek için kaynakları kullanmadan bir veri kaynağından veri sayfası döndürmek için, sorgunuz için yalnızca gerekli olanlarla döndürülen satırları azaltan ek ölçütler belirtin.  
  
 Bir veri sayfası döndürmek için **Fill** metodunu kullanmak için, veri sayfasındaki ilk kayıt Için bir **startRecord** parametresi ve veri sayfasındaki kayıt sayısı için de **MaxRecords** parametresi belirtin.  
  
 Aşağıdaki kod örneği, sayfa boyutunun beş kayıt olduğu bir sorgu sonucunun ilk sayfasını döndürmek için **Fill** yönteminin nasıl kullanılacağını gösterir.  
  
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
  
 Önceki örnekte, **DataSet** yalnızca beş kayıtla doldurulmuştur, ancak tüm **Orders** tablosu döndürülür. **Veri kümesini** aynı beş kayıtla doldurmanız, ancak yalnızca beş kayıt döndürmek için, aşağıdaki kod örneğinde olduğu gibi SQL DEYIMINIZDE top ve WHERE yan tümcelerini kullanın.  
  
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
  
 Sorgu ile disk belleği bu şekilde sonuçlanırsa, aşağıdaki kod örneğinde gösterildiği gibi, bir sonraki kayıt sayfasını döndürmek için özel KIMLIĞI komuta geçirmek üzere satırları sipariş eden benzersiz tanımlayıcıyı korumanız gerektiğini unutmayın.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 **StartRecord** ve **MaxRecords** parametrelerini alan **Fill** yönteminin aşırı yüklemesini kullanarak bir sonraki kayıt sayfasını döndürmek için, geçerli kayıt dizinini sayfa boyutuna göre artırın ve tabloyu girin. **Veri kümesine** yalnızca bir kayıt sayfası eklense bile, veritabanı sunucusunun tüm sorgu sonuçlarını döndürdüğünü unutmayın. Aşağıdaki kod örneğinde, tablo satırları sonraki veri sayfasıyla doldurulmadan önce temizlenir. Veritabanı sunucusuna yapılan gelişleri azaltmak için bir yerel önbellekte belirli sayıda döndürülen satırı korumak isteyebilirsiniz.  
  
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
  
 Veritabanı sunucusunun tüm sorguyu döndürmesi gerekmeden sonraki kayıt sayfasını döndürmek için, SELECT ifadesiyle sınırlayıcı kriterleri belirtin. Yukarıdaki örnek döndürülen son kaydı korunduğu için, aşağıdaki kod örneğinde gösterildiği gibi, sorgu için bir başlangıç noktası belirtmek üzere WHERE yan tümcesinde kullanabilirsiniz.  
  
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
