---
title: DataView Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 9d21b17068ff3ce5b0bd3990144383d7f9ded2f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151344"
---
# <a name="creating-a-dataview"></a>DataView Oluşturma
Bir <xref:System.Data.DataView>. DataView oluşturucuyu kullanabilir veya **'nin** özelliğine <xref:System.Data.DataTable.DefaultView%2A> bir başvuru <xref:System.Data.DataTable>oluşturabilirsiniz. **DataView** oluşturucu boş olabilir veya filtre ölçütleri, sıralama ölçütleri ve satır durumu filtresiyle birlikte bir DataTable'ı tek bir bağımsız değişken olarak veya **DataTable'ı** alabilir. **DataTable** **DataView**ile kullanılabilir ek bağımsız değişkenler hakkında daha fazla bilgi için [bkz.](sorting-and-filtering-data.md)  
  
 **DataView** için dizin hem **DataView** oluşturulduğunda ve **Sıralama,** Satır Filtresi veya **RowStateFilter**özelliklerinden herhangi biri değiştirildiğinde, **DataView'ı**oluştururken herhangi bir ilk sıralama siparişi veya filtreleme ölçütlerini oluşturucu bağımsız değişkenler olarak sağlayarak en iyi performansı elde edeyim. **RowStateFilter** Sıralama veya filtre ölçütleri belirtmeden **bir DataView** oluşturma ve ardından **Sıralama,** **Satır Filtresi**veya **RowStateFilter** özelliklerini ayarlamak daha sonra dizinin en az iki kez oluşturulmasına neden olur: **DataView** oluşturulduğunda ve sıralama veya filtre özelliklerinden herhangi biri değiştirildiğinde tekrar.  
  
 Herhangi bir bağımsız **değişken** kullanmayan bir Veri Görünümü oluşturursanız, **Tablo** özelliğini ayarlayana kadar **DataView'ı** kullanamadığınızı unutmayın.  
  
 Aşağıdaki kod örneği, **DataView** oluşturucuyu kullanarak bir **DataView'ın** nasıl oluşturulabildiğini gösterir. **Bir RowFilter**, **Sıralama** sütunu ve **DataViewRowState** **DataTable**ile birlikte sağlanır.  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],
    "Country = 'USA'",
    "ContactName",
    DataViewRowState.CurrentRows);  
```  
  
 Aşağıdaki kod örneği, tablonun **Varsayılan Görünümü** özelliğini kullanarak bir **DataTable'ın** varsayılan **DataTable Görünümü'ne** nasıl başvuru alınabildiğini gösterir.  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataViews](dataviews.md)
- [Verileri Sıralama ve Filtreleme](sorting-and-filtering-data.md)
- [DataTables](datatables.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
