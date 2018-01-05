---
title: "Seri Hale Getirilebilir Türler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2bf272e785968f9116cea20ad0c3f40eb786d1f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="serializable-types"></a>Seri Hale Getirilebilir Türler
Varsayılan olarak, <xref:System.Runtime.Serialization.DataContractSerializer> tüm herkese görünür türleri serileştirir. Tüm ortak okuma/yazma özellikleri ve türünde alanlar serileştirilir.  
  
 Uygulayarak varsayılan davranışı değiştirebilirsiniz <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelikleri türleri ve üyeleri bu özellik, denetimi altında olmayan ve öznitelikler eklemek için değiştirilemez türlerine sahip durumlarda yararlı olabilir. <xref:System.Runtime.Serialization.DataContractSerializer> "İşaretsiz" gibi türler tanır.  
  
## <a name="serialization-defaults"></a>Seri hale getirme Varsayılanları  
 Uygulayabileceğiniz <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> açıkça denetlemek veya türleri ve üyeleri serileştirme özelleştirmek için öznitelikler. Ayrıca, bu öznitelikler için özel alanlar uygulayabilirsiniz. Ancak, bu özniteliklerle işaretlenmemiş bile türleri seri serisi ve. Aşağıdaki kurallar ve özel durumlar geçerlidir:  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Yeni oluşturulan türlerin varsayılan özellikleri kullanarak özniteliklerini bir veri sözleşmesi türleri oluşturur.  
  
-   Tüm genel alanlar ve ortak özellikleri `get` ve `set` yöntemleri serileştirilir, uyguladığınız sürece <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> özniteliği bu üye için.  
  
-   Seri hale getirme semantiği benzer <xref:System.Xml.Serialization.XmlSerializer>.  
  
-   İşaretsiz türlerinde yalnızca genel tür parametreleri yok oluşturucular ile serileştirilir. Bu kural için özel durum <xref:System.Runtime.Serialization.ExtensionDataObject> ile kullanılan <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi.  
  
-   Salt okunur alan, özellikleri olmadan bir `get` veya `set` yöntemi ve iç veya özel özelliklerle `set` veya `get` yöntemleri sıralanmış değildir. Bu tür özelliklerini göz ardı edilir ve hiçbir özel durum, söz konusu olduğunda yalnızca get koleksiyonları hariç.  
  
-   <xref:System.Xml.Serialization.XmlSerializer>öznitelikler (gibi `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`, vb.) göz ardı edilir.  
  
-   Geçerli <xref:System.Runtime.Serialization.DataContractAttribute> seri hale getirici belirli bir türde özniteliği, bu türün herhangi bir üye göz ardı eder <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği uygulanır.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> Özelliği ile işaretli olmayan türleri desteklenir <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği. Bu desteği içeren <xref:System.Runtime.Serialization.KnownTypeAttribute> işaretsiz türlerinde özniteliği.  
  
-   "Seri hale getirme işlemini Genel üyeler, özellikler veya alanlar için devre dışı bırakmak için", uygulamanız <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> özniteliği bu üye için.  
  
## <a name="inheritance"></a>Devralma  
 İşaretsiz türleri (olmadan türleri <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik) bu özniteliğe sahip türlerinden devrettiği; ancak, geriye doğru izin verilmez: öznitelik türleriyle işaretsiz türlerinden devral olamaz. Bu kural öncelikle'nın önceki sürümlerinde yazılan kod ile geriye dönük uyumluluk sağlamak için zorlanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Veri Anlaşması Seri Hale Getirici Tarafından Desteklenen Türler](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
