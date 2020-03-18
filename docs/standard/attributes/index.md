---
title: Öznitelikleri Kullanarak Meta Verileri Genişletme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- metadata, extending
- attributes [.NET Framework], metadata
- elements [.NET Framework], attributes
- common language runtime, attributes
- annotating programming elements
- keyword-like descriptive declarations
- runtime, attributes
- extending metadata
ms.assetid: 30386922-1e00-4602-9ebf-526b271a8b87
ms.openlocfilehash: b3a106eb58de4865e260a43c8466019e738510f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130897"
---
# <a name="extending-metadata-using-attributes"></a>Öznitelikleri Kullanarak Meta Verileri Genişletme
Ortak dil çalışma süresi, türler, alanlar, yöntemler ve özellikler gibi programlama öğelerine açıklama eklemek için öznitelikler olarak adlandırılan anahtar kelime benzeri açıklayıcı bildirimler eklemenize olanak tanır. Kodunuzu çalışma zamanı için derlediğinizde, microsoft ara diline (MSIL) dönüştürülür ve derleyici tarafından oluşturulan meta verilerle birlikte taşınabilir bir yürütülebilir (PE) dosyasının içine yerleştirilir. Öznitelikler, çalışma zamanı yansıtma hizmetleri kullanılarak ayıklanabilen meta verilere ek açıklayıcı bilgiler yerleştirmenize olanak sağlar. Derleyici, <xref:System.Attribute?displayProperty=nameWithType>'den türeyen özel sınıfların örneklerini bildirdiğinizde öznitelikler oluşturur.  
  
 .NET Framework, çeşitli nedenlerle ve çeşitli sorunları gidermek için öznitelikleri kullanır. Öznitelikler, verilerin nasıl serileştirileceğini açıklar, güvenliği zorlamak için kullanılan özellikleri belirtir ve kodun hata ayıklamanın kolay kalması için tam zamanında (JIT) derleyicitarafından optimizasyonları sınırlandırır. Öznitelikler ayrıca bir dosyanın veya kod yazarının adını kaydedebilir veya form geliştirme sırasında denetimlerin ve üyelerin görünürlüğünü denetleyebilir.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Öznitelikleri Uygulama](../../../docs/standard/attributes/applying-attributes.md)|Kodunuzun bir öğesine nasıl bir öznitelik uygulanacağı açıklanır.|  
|[Özel Öznitelikler Yazma](../../../docs/standard/attributes/writing-custom-attributes.md)|Özel öznitelik sınıfları nasıl tasarlanır açıklar.|  
|[Özniteliklerde Depolanan Bilgileri Alma](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)|Yürütme bağlamına yüklenen kod için özel özniteliklerin nasıl alındığını açıklar.|  
|[Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler](../../../docs/standard/metadata-and-self-describing-components.md)|Meta verilere genel bir bakış sağlar ve .NET Framework taşınabilir çalıştırılabilir (PE) dosyasında nasıl uygulandığını açıklar.|  
|[Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Yalnızca yansıma bağlamında özel öznitelik bilgilerinin nasıl alındığını açıklar.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Attribute?displayProperty=nameWithType>
