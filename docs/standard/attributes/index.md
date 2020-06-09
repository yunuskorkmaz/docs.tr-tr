---
title: Öznitelikleri Kullanarak Meta Verileri Genişletme
description: .NET 'teki öznitelikleri kullanarak meta verileri genişletmeyi öğrenin. Öznitelikler, türler ve alanlar gibi programlama öğelerine açıklama eklemek için anahtar sözcük benzeri açıklayıcı bildirimlerdir.
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
ms.openlocfilehash: c77de970c5550bd896e83854414592d70eb9dc48
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598638"
---
# <a name="extending-metadata-using-attributes"></a>Öznitelikleri Kullanarak Meta Verileri Genişletme
Ortak dil çalışma zamanı, türler, alanlar, Yöntemler ve özellikler gibi programlama öğelerine açıklama eklemek için öznitelikler olarak adlandırılan anahtar sözcük benzeri açıklayıcı bildirimler eklemenize olanak tanır. Çalışma zamanı için kodunuzu derlerken, Microsoft ara dili 'ne (MSIL) dönüştürülür ve derleyici tarafından oluşturulan meta verilerle birlikte taşınabilir bir çalıştırılabilir (PE) dosyası içine konur. Öznitelikleri, çalışma zamanı yansıma Hizmetleri kullanılarak ayıklanabilen meta verilere fazladan açıklayıcı bilgiler yerleştirmenizi sağlar. Derleyici, sınıfından türetilen özel sınıfların örneklerini bildirdiğinizde öznitelikler oluşturur <xref:System.Attribute?displayProperty=nameWithType> .  
  
 .NET Framework çeşitli nedenlerle öznitelikler kullanır ve bir dizi sorunu ele almak için kullanılır. Öznitelikler, verilerin serileştirilmesi, güvenliği zorlamak için kullanılan özellikleri belirtmek ve tam zamanında (JıT) derleyicisine yönelik iyileştirmeleri sınırlamak için kodun kolayca hata ayıklaması gerektiğini anlatmaktadır. Öznitelikler Ayrıca, bir dosyanın veya kod yazarının adını kaydedebilir veya form geliştirme sırasında denetimlerin ve üyelerin görünürlüğünü denetleyebilir.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Öznitelikleri Uygulama](applying-attributes.md)|Kodunuzun bir öğesine nasıl öznitelik uygulanacağını açıklar.|  
|[Özel Öznitelikler Yazma](writing-custom-attributes.md)|Özel öznitelik sınıflarının nasıl tasarlanacağını açıklar.|  
|[Özniteliklerde Depolanan Bilgileri Alma](retrieving-information-stored-in-attributes.md)|Yürütme bağlamına yüklenen kod için özel özniteliklerin nasıl alınacağını açıklar.|  
|[Meta veriler ve kendi kendine açıklama bileşenleri](../metadata-and-self-describing-components.md)|Meta verilere genel bakış sağlar ve .NET Framework taşınabilir yürütülebilir (PE) dosyasında nasıl uygulandığını açıklar.|  
|[Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Özel öznitelik bilgilerinin yalnızca yansıma bağlamında nasıl alınacağını açıklar.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Attribute?displayProperty=nameWithType>
