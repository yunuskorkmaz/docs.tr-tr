---
title: DataView Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 391c071f19149e9690c9121b1094aef5bfa605cd
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203832"
---
# <a name="creating-a-dataview"></a>DataView Oluşturma
Oluşturmak için iki yol vardır <xref:System.Data.DataView>. **DataView** oluşturucusunu kullanabilir veya <xref:System.Data.DataTable.DefaultView%2A> özelliğine <xref:System.Data.DataTable>bir başvuru oluşturabilirsiniz. **DataView** Oluşturucusu boş olabilir veya tek bir bağımsız değişken olarak bir **DataTable** ya da filtre ölçütü, sıralama ölçütü ve bir satır durumu filtresiyle birlikte bir DataTable alabilir. **DataView**ile kullanılabilecek ek bağımsız değişkenler hakkında daha fazla bilgi için bkz. [verileri sıralama ve filtreleme](sorting-and-filtering-data.md).  
  
 DataView dizini her ikisi de **DataView** oluşturulduğunda oluşturulduğundan ve **sıralama**, **RowFilter**veya **RowStateFilter** özelliklerinden herhangi biri değiştirildiğinde, herhangi bir başlangıç sağlayarak en iyi performansı elde edersiniz **DataView**oluştururken Oluşturucu bağımsız değişkenleri olarak sıralamayı veya filtreleme ölçütlerini sıralayın. Sıralama veya filtre ölçütlerini belirtmeden bir **DataView** oluşturma, sonra **sıralama**, **RowFilter**veya **RowStateFilter** özelliklerinin daha sonra ayarlanması dizinin en az iki kez oluşturulmasına neden olur: **DataView** olduğunda sıralama veya filtre özelliklerinden herhangi biri değiştirildiğinde, ve yeniden oluşturulur.  
  
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
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
