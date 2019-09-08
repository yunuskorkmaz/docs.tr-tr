---
title: Verileri Sıralama ve Filtreleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 09cee2f2b2c3288c835912c9f311bf2511c7b0d0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785919"
---
# <a name="sorting-and-filtering-data"></a>Verileri Sıralama ve Filtreleme
, <xref:System.Data.DataView> Bir<xref:System.Data.DataTable>içindeki verileri sıralamak ve filtrelemek için çeşitli yollar sağlar:  
  
- <xref:System.Data.DataView.Sort%2A> Özelliğini kullanarak tek veya birden çok sütun sıralama düzeni belirtebilir ve ASC (artan) ve DESC (azalan) parametreleri dahil edebilirsiniz.  
  
- <xref:System.Data.DataView.ApplyDefaultSort%2A> Özelliğini, tablonun birincil anahtar sütununa veya sütunlarına göre artan sırada otomatik olarak bir sıralama düzeni oluşturmak için kullanabilirsiniz. <xref:System.Data.DataView.ApplyDefaultSort%2A>yalnızca **sıralama** özelliği null veya boş bir dize olduğunda ve tablonun tanımlı bir birincil anahtarı olduğunda geçerlidir.  
  
- Özelliğini, <xref:System.Data.DataView.RowFilter%2A> sütun değerlerine göre satır alt kümelerini belirtmek için kullanabilirsiniz. **RowFilter** özelliği için geçerli ifadeler hakkında daha fazla bilgi için, <xref:System.Data.DataColumn.Expression%2A> <xref:System.Data.DataColumn> sınıfının özelliği için başvuru bilgilerine bakın.  
  
     Verilerin bir alt kümesinin dinamik bir görünümünü sağlamanın aksine, veriler üzerinde belirli bir sorgunun sonuçlarını döndürmek istiyorsanız, şu şekilde ayarlamak <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> **yerine en iyi performansı elde etmek için DataView 'ın veya yöntemlerini kullanın RowFilter** özelliği. **RowFilter** özelliğinin ayarlanması, verilerin dizinini yeniden oluşturur, uygulamanıza ek yük ekler ve performansı azaltır. **RowFilter** özelliği, bir bağlantılı denetimin filtrelenmiş sonuçları görüntülediği veriye dayalı bir uygulamada en iyi şekilde kullanılır. **Find** ve **FindRows** yöntemleri, dizinin yeniden oluşturulmasını gerektirmeden geçerli dizinden yararlanır. **Find** ve **FindRows** yöntemleri hakkında daha fazla bilgi Için bkz. [satırları bulma](finding-rows.md).  
  
- Hangi satır sürümlerinin görüntüleneceği <xref:System.Data.DataView.RowStateFilter%2A> belirlemek için özelliğini kullanabilirsiniz. **DataView** , temel alınan satırın **RowState** öğesine bağlı olarak hangi satır sürümünün sergileceğini dolaylı olarak yönetir. Örneğin, **RowStateFilter** , **DataViewRowState. Deleted**olarak ayarlandıysa, **geçerli** satır sürümü bulunmadığından **DataView** , **silinen** tüm satırların **orijinal** satır sürümünü kullanıma sunar. **DataRowView**'ın **ROWVERSION** özelliğini kullanarak bir satırın hangi satır sürümünün gösterilmesini belirleyebilirsiniz.  
  
     Aşağıdaki tabloda, **DataViewRowState**seçenekleri gösterilmektedir.  
  
    |DataViewRowState seçenekleri|Açıklama|  
    |------------------------------|-----------------|  
    |**CurrentRows**|Tüm **değişmemiş**, **eklenen**ve **değiştirilen** satırların **geçerli** satır sürümü. Bu varsayılandır.|  
    |**Eklenirse**|Tüm **eklenen** satırların **geçerli** satır sürümü.|  
    |**Miyor**|**Silinen** tüm satırların **orijinal** satır sürümü.|  
    |**ModifiedCurrent**|**Değiştirilen** tüm satırların **geçerli** satır sürümü.|  
    |**Modifiedorijinal**|**Değiştirilen** tüm satırların **orijinal** satır sürümü.|  
    |**Yok.**|Satır yok.|  
    |**OriginalRows**|Tüm **değişmemiş**, **değiştirilen**ve **silinen** satırların **orijinal** satır sürümü.|  
    |**Değiştirilmediği**|**Değişmeyen** tüm satırların **geçerli** satır sürümü.|  
  
 Satır durumları ve satır sürümleri hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).  
  
 Aşağıdaki kod örneği, stoktaki birim sayısının yeniden sipariş düzeyine eşit veya daha küçük olduğu, önce Tedarikçi KIMLIĞI ve ardından ürün adına göre sıralanmış tüm ürünleri gösteren bir görünüm oluşturur.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataViews](dataviews.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
