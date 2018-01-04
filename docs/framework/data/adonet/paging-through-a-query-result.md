---
title: "Sorgu sonucu disk belleği"
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
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 506458eab146614f505a5558cd3535f06aecb83c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="paging-through-a-query-result"></a>Sorgu sonucu disk belleği
Disk belleği sorgu sonucu aracılığıyla veri veya sayfalarının daha küçük alt kümeler halinde bir sorgunun sonuçlarını döndürme işlemidir. Bu küçük, yönetilmesi kolay öbekleri bir kullanıcıya sonuçları görüntülemek için yaygın bir uygulamadır.  
  
 **DataAdapter** yalnızca bir sayfa aşırı aracılığıyla veri döndürmek için bir olanağı sağlar **doldurun** yöntemi. Ancak, bu büyük sorgu sonuçları olduğundan, disk belleği en iyi seçenek olmayabilir rağmen **DataAdapter** hedef doldurur <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> kayıtlarla yalnızca istenen, geri dönmek için kaynaklar tüm sorgu hala kullanılır. Tüm sorgu döndürülecek kaynakların kullanmadan bir veri kaynağından veri sayfasının dönmek için yalnızca bu gerekli döndürülen satır azaltan ek sorgunuzu ölçütleri belirtin.  
  
 Kullanılacak **doldurun** , verilerin bir sayfaya dönmek için yöntemi belirtin bir **startRecord** veri sayfasındaki ilk kaydı için parametre ve bir **maxRecords** parametre sayısı veri sayfasındaki kaydeder.  
  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir **doldurun** sayfa boyutu beş kayıt olduğu bir sorgu sonucunun ilk sayfasına dönmek için yöntem.  
  
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
  
 Önceki örnekte, **DataSet** yalnızca beş kaydeder, ancak tüm ile doldurulur **siparişleri** tablo döndürülür. Doldurmak için **DataSet** aynı beş kayıtları, ancak yalnızca dönüş beş kayıt, üst kullanın ve aşağıdaki kod örneğinde olduğu gibi SQL deyimindeki WHERE yan tümcelerini.  
  
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
  
 Bu şekilde sorgu sonuçlarında üzerinden disk belleği, benzersiz kimliği kayıtlarının, sonraki sayfaya dönmek için komutu aşağıdaki kod örneğinde gösterildiği gibi geçirmek için satır siparişleri benzersiz tanımlayıcı korumak, unutmayın.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 Aşırı yüklemesini kullanarak kayıtların sonraki sayfaya dönmek için **doldurun** yönteminin alan **startRecord** ve **maxRecords** parametreleri, geçerli kayıt dizini tarafından Artır Sayfa boyutunu ve doldurma tablo. Veritabanı sunucusu yalnızca bir sayfa kaydı eklenir olsa bile tüm sorgu sonuçlarını döndürür unutmayın **DataSet**. Veri sonraki sayfa ile doldurulur önce aşağıdaki kod örneğinde tablo satırları temizlenir. Belirli bir veritabanı sunucusuna dönüşleri azaltmasını için yerel önbellekteki döndürülen satır sayısını korumak isteyebilirsiniz.  
  
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
  
 Tüm sorgu döndürme veritabanı sunucusu olmadan kayıtların sonraki sayfaya dönmek için SELECT deyimi kısıtlayıcı ölçütü belirtin. Önceki örnekte döndürülen son kaydı korunur olduğundan, WHERE yan tümcesinde sorgu için bir başlangıç noktası belirtmek için aşağıdaki kod örneğinde gösterildiği gibi kullanabilirsiniz.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
