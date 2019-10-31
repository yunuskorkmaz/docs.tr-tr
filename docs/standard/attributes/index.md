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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130897"
---
# <a name="extending-metadata-using-attributes"></a>Öznitelikleri Kullanarak Meta Verileri Genişletme
Ortak dil çalışma zamanı, türler, alanlar, Yöntemler ve özellikler gibi programlama öğelerine açıklama eklemek için öznitelikler olarak adlandırılan anahtar sözcük benzeri açıklayıcı bildirimler eklemenize olanak tanır. Çalışma zamanı için kodunuzu derlerken, Microsoft ara dili 'ne (MSIL) dönüştürülür ve derleyici tarafından oluşturulan meta verilerle birlikte taşınabilir bir çalıştırılabilir (PE) dosyası içine konur. Öznitelikleri, çalışma zamanı yansıma Hizmetleri kullanılarak ayıklanabilen meta verilere fazladan açıklayıcı bilgiler yerleştirmenizi sağlar. Derleyici, <xref:System.Attribute?displayProperty=nameWithType>türetilen özel sınıfların örneklerini bildirdiğinizde öznitelikler oluşturur.  
  
 .NET Framework çeşitli nedenlerle öznitelikler kullanır ve bir dizi sorunu ele almak için kullanılır. Öznitelikler, verilerin serileştirilmesi, güvenliği zorlamak için kullanılan özellikleri belirtmek ve tam zamanında (JıT) derleyicisine yönelik iyileştirmeleri sınırlamak için kodun kolayca hata ayıklaması gerektiğini anlatmaktadır. Öznitelikler Ayrıca, bir dosyanın veya kod yazarının adını kaydedebilir veya form geliştirme sırasında denetimlerin ve üyelerin görünürlüğünü denetleyebilir.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Öznitelikleri Uygulama](../../../docs/standard/attributes/applying-attributes.md)|Kodunuzun bir öğesine nasıl öznitelik uygulanacağını açıklar.|  
|[Özel Öznitelikler Yazma](../../../docs/standard/attributes/writing-custom-attributes.md)|Özel öznitelik sınıflarının nasıl tasarlanacağını açıklar.|  
|[Özniteliklerde Depolanan Bilgileri Alma](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)|Yürütme bağlamına yüklenen kod için özel özniteliklerin nasıl alınacağını açıklar.|  
|[Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler](../../../docs/standard/metadata-and-self-describing-components.md)|Meta verilere genel bakış sağlar ve .NET Framework taşınabilir yürütülebilir (PE) dosyasında nasıl uygulandığını açıklar.|  
|[Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Özel öznitelik bilgilerinin yalnızca yansıma bağlamında nasıl alınacağını açıklar.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Attribute?displayProperty=nameWithType>
