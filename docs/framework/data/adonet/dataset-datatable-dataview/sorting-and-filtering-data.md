---
title: Verileri sıralama ve filtreleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 02a67a490eb8339663aac08c97c665ffee09f0df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760615"
---
# <a name="sorting-and-filtering-data"></a>Verileri sıralama ve filtreleme
<xref:System.Data.DataView> Sıralama ve filtreleme verileri çeşitli yollar sağlar bir <xref:System.Data.DataTable>:  
  
-   Kullanabileceğiniz <xref:System.Data.DataView.Sort%2A> tek belirtmek için özellik veya sıralama siparişleri ve ASC (artan) ve (Azalan) DESC parametreleri dahil birden fazla sütun.  
  
-   Kullanabileceğiniz <xref:System.Data.DataView.ApplyDefaultSort%2A> artan sırada bir sıralama düzeni otomatik olarak oluşturmak için özelliğini temel tablosunun sütunlarını ve birincil anahtar sütunu üzerinde. <xref:System.Data.DataView.ApplyDefaultSort%2A> yalnızca aşağıdaki durumlarda uygulanır **sıralama** özelliği olan bir null başvuru ya da boş bir dize ve ne zaman tablonun tanımlı bir birincil anahtara sahip.  
  
-   Kullanabileceğiniz <xref:System.Data.DataView.RowFilter%2A> satır kümelerine belirtmek üzere özelliğe dayalı sütun değerlerine göre. İçin geçerli ifadeler hakkında ayrıntılı bilgi için **RowFilter** özelliği, başvuru bilgileri için bkz <xref:System.Data.DataColumn.Expression%2A> özelliği <xref:System.Data.DataColumn> sınıfı.  
  
     Bir veri alt kümesini dinamik bir görünümünü sağlayarak verileri üzerinde belirli bir sorgu sonuçlarını kullanmak dönmek istiyorsanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemlerinin **DataView** en iyi performans elde etmek için yerine ayarı **RowFilter** özelliği. Ayarı **RowFilter** özelliği veri yükü uygulamanıza ekleme ve performans azaltmak için dizini yeniden oluşturur. **RowFilter** özelliği en iyi kullanılır verilere bağlı uygulamada burada bağlantılı denetim filtrelenen sonuçları görüntüler. **Bul** ve **FindRows** yöntemleri yeniden oluşturulması için dizin gerek kalmadan geçerli dizini yararlanın. Hakkında daha fazla bilgi için **Bul** ve **FindRows** yöntemleri bkz [bulma satırları](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
-   Kullanabileceğiniz <xref:System.Data.DataView.RowStateFilter%2A> özelliği görüntülemek için hangi satır sürümlerini belirtin. **DataView** dolaylı olarak bağlı olarak kullanıma sunmak için hangi satır sürümü yönetir **RowState** temel satır. Örneğin, varsa **RowStateFilter** ayarlanır **DataViewRowState.Deleted**, **DataView** sunan **özgün** satır sürümü tüm **silinmiş** olduğundan satırları hiçbir **geçerli** satır sürümü. Hangi satır sürümü satır kullanarak yararlanılmasını belirleyebilirsiniz **RowVersion** özelliği **DataRowView**.  
  
     Aşağıdaki tabloda seçeneklerini gösterir **DataViewRowState**.  
  
    |DataViewRowState seçenekleri|Açıklama|  
    |------------------------------|-----------------|  
    |**CurrentRows**|**Geçerli** tüm satır sürümü **Unchanged**, **eklenen**, ve **değiştirilen** satır. Bu varsayılandır.|  
    |**Eklenen**|**Geçerli** tüm satır sürümü **eklenen** satır.|  
    |**silindi**|**Özgün** tüm satır sürümü **silinmiş** satır.|  
    |**ModifiedCurrent**|**Geçerli** tüm satır sürümü **değiştirilen** satır.|  
    |**ModifiedOriginal**|**Özgün** tüm satır sürümü **değiştirilen** satır.|  
    |**Yok**|Satır yok.|  
    |**OriginalRows**|**Özgün** tüm satır sürümü **Unchanged**, **değiştirilen**, ve **silinmiş** satır.|  
    |**Değişmedi**|**Geçerli** tüm satır sürümü **Unchanged** satır.|  
  
 Satır durumları ve satır sürümleri hakkında daha fazla bilgi için bkz: [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 Aşağıdaki kod örneğinde gösterildiği stoktaki birim sayısını sipariş düzeyine eşit veya daha az olduğu tüm ürünleri sıralanmış sağlayıcı kimliği ve ardından ürün adına göre ilk bir görünüm oluşturur.  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
