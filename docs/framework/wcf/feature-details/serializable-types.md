---
title: Seri Hale Getirilebilir Türler
ms.date: 03/30/2017
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
ms.openlocfilehash: e65fcb93c5c36bb289b825cef58b3adc6f5155f5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586110"
---
# <a name="serializable-types"></a>Seri Hale Getirilebilir Türler
Varsayılan olarak, <xref:System.Runtime.Serialization.DataContractSerializer> tüm herkese açık görünen türler seri hale getirir. Türün tüm genel okuma/yazma özellikleri ve alanları serileştirilir.  
  
 <xref:System.Runtime.Serialization.DataContractAttribute>Ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliklerini türlerine ve üyelerine uygulayarak varsayılan davranışı değiştirebilirsiniz. Bu özellik, denetiminizin altında olmayan türlerinizin bulunduğu durumlarda yararlı olabilir ve öznitelik eklemek için değiştirilemez. <xref:System.Runtime.Serialization.DataContractSerializer>Bu tür "işaretsiz" türleri tanır.  
  
## <a name="serialization-defaults"></a>Serileştirme Varsayılanları  
 <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> Türlerin ve üyelerin serileştirmesini açıkça denetlemek veya özelleştirmek için ve özniteliklerini uygulayabilirsiniz. Ayrıca, bu öznitelikleri özel alanlara de uygulayabilirsiniz. Ancak, bu özniteliklerle işaretlenmeyen türler bile serileştirilir ve seri durumdan çıkarılamaz. Aşağıdaki kurallar ve özel durumlar geçerlidir:  
  
- , <xref:System.Runtime.Serialization.DataContractSerializer> Yeni oluşturulan türlerin varsayılan özelliklerini kullanarak öznitelikleri olmayan türlerden bir veri sözleşmesini ele anlar.  
  
- `get` `set` Özniteliği bu üyeye uygulamadığınız takdirde ortak ve yöntemlere sahip tüm genel alanlar ve Özellikler sıralanır <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> .  
  
- Serileştirme semantiği ile benzerdir <xref:System.Xml.Serialization.XmlSerializer> .  
  
- İşaretsiz türlerde, yalnızca parametreleri olmayan oluşturuculara sahip ortak türler serileştirilir. Bu kuralın özel durumu <xref:System.Runtime.Serialization.ExtensionDataObject> arabirimle birlikte kullanılır <xref:System.Runtime.Serialization.IExtensibleDataObject> .  
  
- Salt okuma alanları, or yöntemi olmayan özellikler `get` `set` ve iç ya da özel `set` veya yöntemlerle Özellikler `get` serileştirilmez. Bu tür özellikler yok sayılır ve salt al koleksiyonlar olması dışında hiçbir özel durum oluşturulmaz.  
  
- <xref:System.Xml.Serialization.XmlSerializer>Öznitelikler (örneğin,,,, vb `XmlElement` `XmlAttribute` `XmlIgnore` `XmlInclude` .) yoksayılır.  
  
- <xref:System.Runtime.Serialization.DataContractAttribute>Özniteliği belirli bir türe uygulamazsanız, seri hale getirici özniteliğin uygulandığı bu türdeki herhangi bir üyeyi yoksayar <xref:System.Runtime.Serialization.DataMemberAttribute> .  
  
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>Özelliği, özniteliğiyle işaretlenmemiş türlerde desteklenir <xref:System.Runtime.Serialization.DataContractAttribute> . Bu, <xref:System.Runtime.Serialization.KnownTypeAttribute> işaretsiz türlerde özniteliği için destek içerir.  
  
- Ortak Üyeler, özellikler veya alanlar için serileştirme işleminin "kabul etmek" için, <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> Bu üyeye özniteliğini uygulayın.  
  
## <a name="inheritance"></a>Devralma  
 İşaretsiz türler (özniteliği olmayan türler <xref:System.Runtime.Serialization.DataContractAttribute> ), bu özniteliğe sahip olan türlerden devralınabilir; ancak, ters izin verilmez: özniteliği olan türler işaretsiz türlerden devralınabilir. Bu kural öncelikle .NET Framework önceki sürümlerinde yazılmış kodla geriye dönük uyumluluk sağlamak için zorlanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Veri Sözleşmesi Seri Hale Getirici Tarafından Desteklenen Türler](types-supported-by-the-data-contract-serializer.md)
