---
title: Verileri sıralama ve filtreleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: ade08deca909b32090b7d2d7cf8c6ba9ce9e7679
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083136"
---
# <a name="sorting-and-filtering-data"></a>Verileri sıralama ve filtreleme
<xref:System.Data.DataView> İçindeki verileri sıralama ve filtreleme çeşitli yollarını sağlar bir <xref:System.Data.DataTable>:  
  
-   Kullanabileceğiniz <xref:System.Data.DataView.Sort%2A> tek belirtmek için özelliği veya sıralama düzenlerine ve ASC (artan) ve (Azalan) DESC parametreleri içeren birden çok sütunu.  
  
-   Kullanabileceğiniz <xref:System.Data.DataView.ApplyDefaultSort%2A> özelliği otomatik olarak bir sıralama düzeni artan düzende oluşturmak için temel tablonun sütunlarının ve birincil anahtar sütunu üzerinde. <xref:System.Data.DataView.ApplyDefaultSort%2A> yalnızca geçerli **sıralama** özelliği null bir başvuru ya da boş bir dize ve tabloda bir birincil anahtar tanımlı olduğunda.  
  
-   Kullanabileceğiniz <xref:System.Data.DataView.RowFilter%2A> satır kümelerine belirtmek için özellik sütun değerlerine bağlı. İçin geçerli ifadeler hakkında daha fazla ayrıntı için **RowFilter** özelliğine başvuru bilgilerine bakın <xref:System.Data.DataColumn.Expression%2A> özelliği <xref:System.Data.DataColumn> sınıfı.  
  
     Verilerin bir alt kümesini, dinamik bir görünüm sağlayarak veriler üzerinde belirli bir sorgu sonuçlarını kullanma dönmek istiyorsanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemlerinin **DataView** en iyi performans elde etmek için değil ayarı **RowFilter** özelliği. Ayarı **RowFilter** özelliği yükü uygulamanıza ekleme ve performansı azaltarak veri dizini oluşturur. **RowFilter** özelliği en iyi şekilde kullanılır verilere bağlı uygulamada nereye bağlantılı denetim filtrelenmiş sonuçları görüntüler. **Bul** ve **FindRows** yöntemleri, yeniden oluşturulması için dizini gerek kalmadan geçerli dizini yararlanın. Hakkında daha fazla bilgi için **Bul** ve **FindRows** yöntemleri bkz [satırları bulma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
-   Kullanabileceğiniz <xref:System.Data.DataView.RowStateFilter%2A> özelliği görüntülemek için hangi satır sürümleri belirtin. **DataView** örtük olarak bağlı olarak kullanıma sunmak için hangi satır sürümünü yönetir **RowState** temel alınan satır. Örneğin, varsa **RowStateFilter** ayarlanır **DataViewRowState.Deleted**, **DataView** sunan **özgün** satır sürümü tüm **silinmiş** olduğundan satırları hiçbir **geçerli** satır sürümü. Satır hangi satır sürümünü kullanarak açıklanmasını belirlemek **RowVersion** özelliği **DataRowView**.  
  
     Aşağıdaki tabloda ilişkin seçenekler gösterilir **DataViewRowState**.  
  
    |DataViewRowState seçenekleri|Açıklama|  
    |------------------------------|-----------------|  
    |**CurrentRows**|**Geçerli** satır sürümü tüm **Unchanged**, **eklenen**, ve **değiştirilen** satır. Bu varsayılandır.|  
    |**Eklendi**|**Geçerli** satır sürümü tüm **eklenen** satır.|  
    |**silindi**|**Özgün** satır sürümü tüm **silinmiş** satır.|  
    |**ModifiedCurrent**|**Geçerli** satır sürümü tüm **değiştirilen** satır.|  
    |**ModifiedOriginal**|**Özgün** satır sürümü tüm **değiştirilen** satır.|  
    |**Yok**|Satır yok.|  
    |**OriginalRows**|**Özgün** satır sürümü tüm **Unchanged**, **değiştirilen**, ve **silinmiş** satır.|  
    |**değişmedi**|**Geçerli** satır sürümü tüm **Unchanged** satır.|  
  
 Satır durumları ve satır sürümleri hakkında daha fazla bilgi için bkz. [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 Aşağıdaki kod örneği, stoktaki birim sayısını ya da yeniden sıralama düzeyi eşit olduğu tüm ürünleri gösterir sıralanmış sağlayıcı kimliği ve ardından ürün adına göre öncelikle bir görünüm oluşturur.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
