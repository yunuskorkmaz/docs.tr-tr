---
title: Seri Hale Getirilebilir Türler
ms.date: 03/30/2017
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
ms.openlocfilehash: 44fc538ccb69296b91c94d2b9ae497be599c0c7e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160855"
---
# <a name="serializable-types"></a>Seri Hale Getirilebilir Türler
Varsayılan olarak, <xref:System.Runtime.Serialization.DataContractSerializer> tüm herkese görünür türler seri hale getirir. Tüm ortak okuma/yazma özellikleri ve türünde alanlar serileştirilir.  
  
 Uygulayarak, varsayılan davranışı değiştirebilirsiniz <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelikleri türler ve üyeler için bu özellik, denetiminde değildir ve öznitelikler eklemek için değiştirilemez türlerine sahip durumlarda yararlı olabilir. <xref:System.Runtime.Serialization.DataContractSerializer> "İşaretsiz" gibi türlerini tanır.  
  
## <a name="serialization-defaults"></a>Serileştirme Varsayılanları  
 Uygulayabileceğiniz <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> açıkça denetlemek veya tür ve üyelerinin seri hale getirme özelleştirmek için öznitelikleri. Ayrıca, özel alanları bu öznitelikleri uygulayabilirsiniz. Ancak, bu öznitelikleri ile işaretlenmemiş türler bile serileştirilmiş seri durumdan ve. Aşağıdaki kurallar ve özel durumlar geçerlidir:  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Öznitelikleri yeni oluşturulan türlerinin varsayılan özelliklerini kullanarak bir veri anlaşması türlerinden algılar.  
  
-   Tüm genel alanlar ve Özellikler ortak `get` ve `set` yöntemleri serileştirilme, uyguladığınız sürece <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> özniteliği bu üye için.  
  
-   Serileştirme semantiği gereksinimlerine benzer <xref:System.Xml.Serialization.XmlSerializer>.  
  
-   Yalnızca genel tür parametreleri olmayan oluşturucular ile işaretlenmemiş türlerinde serileştirilir. Bu kuralın istisnası <xref:System.Runtime.Serialization.ExtensionDataObject> ile kullanılan <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi.  
  
-   Salt okunur alanlar, özellikler olmadan bir `get` veya `set` yöntemi ve iç veya özel özelliklerle `set` veya `get` yöntemleri seri değildir. Bu tür özelliklerini göz ardı edilir ve hiçbir özel durum, söz konusu olduğunda salt alma koleksiyon hariç.  
  
-   <xref:System.Xml.Serialization.XmlSerializer> öznitelikler (gibi `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`, vb.) göz ardı edilir.  
  
-   Geçerli <xref:System.Runtime.Serialization.DataContractAttribute> verilen tür, seri hale getirici özniteliği bu türün herhangi bir üyesi yok sayar <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği uygulanır.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> Özelliği ile işaretlenmemiş türlerinde desteklenir <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği. Buna aşağıdakilerin desteklenmesi dahildir <xref:System.Runtime.Serialization.KnownTypeAttribute> işaretsiz türleri özniteliği.  
  
-   "Seri hale getirme işlemi Genel üyeler, özellikler veya alanlar için geri çevirmek için", geçerli <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> özniteliği bu üye için.  
  
## <a name="inheritance"></a>Devralma  
 İşaretsiz türleri (olmadan türleri <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği) bu özniteliği olan türlerinden devraldığına; ancak tersi izin verilmez: öznitelik türleriyle işaretsiz türlerden devralamaz. Bu kural öncelikle'nın önceki sürümlerinde yazılan kod ile geriye dönük uyumluluk sağlamak için zorunlu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Veri Sözleşmesi Seri Hale Getirici Tarafından Desteklenen Türler](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
