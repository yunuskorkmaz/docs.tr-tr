---
title: DataView Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 539e9763c8aa4affdb6f3bd219a99dbca50cee01
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202350"
---
# <a name="creating-a-dataview"></a>DataView Oluşturma

Oluşturmak için iki yol vardır <xref:System.Data.DataView> . **DataView** oluşturucusunu kullanabilir veya özelliğine bir başvuru oluşturabilirsiniz <xref:System.Data.DataTable.DefaultView%2A> <xref:System.Data.DataTable> . **DataView** Oluşturucusu boş olabilir veya tek bir bağımsız değişken olarak bir **DataTable** ya da filtre ölçütü, sıralama ölçütü ve bir satır durumu **filtresiyle birlikte bir DataTable alabilir** . **DataView**ile kullanılabilecek ek bağımsız değişkenler hakkında daha fazla bilgi için bkz. [verileri sıralama ve filtreleme](sorting-and-filtering-data.md).  
  
 **DataView dizini** her Ikisi de **DataView** oluşturulduğunda oluşturulduğundan ve **sıralama**, **RowFilter**veya **RowStateFilter** özelliklerinin herhangi biri değiştirildiğinde, **DataView**oluştururken Oluşturucu bağımsız değişken olarak herhangi bir ilk sıralama düzeni veya filtreleme ölçütü sağlayarak en iyi performansı elde edersiniz. Sort veya Filter ölçütlerini belirtmeden bir **DataView** oluşturma, sonra **sıralama**, **RowFilter**veya **RowStateFilter** özelliklerini ayarlama, dizinin en az iki kez oluşturulmasına neden olur: **DataView** oluşturulduğunda ve sıralama ya da filtre özelliklerinden herhangi biri değiştirildiğinde yeniden.  
  
 Herhangi bir bağımsız değişken kullanmayan oluşturucuyu kullanarak bir **DataView** oluşturursanız, **tablo** özelliği ayarlanana kadar **DataView** 'ı kullanabileceksiniz.  
  
 Aşağıdaki kod örneği, **DataView** oluşturucuyu kullanarak bir **DataView** oluşturmayı gösterir. **DataTable**Ile birlikte **RowFilter**, **Sort** sütunu ve **DataViewRowState** sağlanır.  
  
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
  
 Aşağıdaki kod örneği, tablosunun **DefaultView** özelliğini kullanarak bir **DataTable** 'ın varsayılan **DataView** öğesine nasıl başvuru alınacağını göstermektedir.  
  
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
