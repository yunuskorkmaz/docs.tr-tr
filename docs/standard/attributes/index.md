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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a31082604048e71ebc7581b36857a8bfbd333c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969799"
---
# <a name="extending-metadata-using-attributes"></a>Öznitelikleri Kullanarak Meta Verileri Genişletme
Ortak dil çalışma zamanı, anahtar sözcük benzeri tanımlayıcı bildirimler eklemenize olanak sağlar, türleri, alanları, yöntemleri ve özellikleri gibi programlama öğesine açıklama eklemek için öznitelikler çağrılır. Çalışma zamanı için kodunuzu derlediğinizde, Microsoft Ara diline (MSIL) dönüştürülür ve derleyici tarafından oluşturulan meta verilerinin yanı sıra bir taşınabilir yürütülebilir (PE) dosya içine yerleştirilir. Öznitelikler, çalışma zamanı yansıma Hizmetleri kullanarak ayıklanan meta verileri fazladan açıklayıcı bilgileri yerleştirin olanak tanır. Öğesinden türetilen özel sınıfların örneklerini bildirdiğinizde, derleyici öznitelikleri oluşturur <xref:System.Attribute?displayProperty=nameWithType>.  
  
 .NET Framework çeşitli nedenleri ve birkaç sorun gidermenin için öznitelikleri kullanır. Verileri seri hale getirme, güvenliği zorlamak için kullanılan özellikleri belirtin ve kod hatalarını ayıklamak kolay kalır. böylece, en iyi duruma getirme just-ın-time (JIT) derleyici tarafından sınırlamak nasıl özniteliklerini açıklar. Öznitelikleri ayrıca bir dosyanın adı ve kod yazarı kaydetmek, veya forms geliştirme sırasında denetimleri ve üyeleri görünürlüğünü denetleme.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Öznitelikleri Uygulama](../../../docs/standard/attributes/applying-attributes.md)|Kodunuzun bir öğeye bir öznitelik uygulamak açıklar.|  
|[Özel Öznitelikler Yazma](../../../docs/standard/attributes/writing-custom-attributes.md)|Özel öznitelik sınıfları tasarlama konularını açıklar.|  
|[Özniteliklerde Depolanan Bilgileri Alma](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)|Yürütme bağlamı yüklenen kod için özel öznitelikler alınacağını açıklar.|  
|[Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler](../../../docs/standard/metadata-and-self-describing-components.md)|Meta veri genel bir bakış sağlar ve bir .NET Framework taşınabilir yürütülebilir (PE) dosyasında nasıl uygulandığı açıklanmaktadır.|  
|[Nasıl yapılır: Salt yansıma bağlamına derlemeleri yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Yalnızca yansıma içeriğinde özel öznitelik bilgileri almak açıklanmaktadır.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Attribute?displayProperty=nameWithType>
