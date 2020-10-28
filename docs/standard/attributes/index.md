---
title: Öznitelikleri Kullanarak Meta Verileri Genişletme
description: .NET 'teki öznitelikleri kullanarak meta verileri genişletmeyi öğrenin. Öznitelikler, türler ve alanlar gibi programlama öğelerine açıklama eklemek için anahtar sözcük benzeri açıklayıcı bildirimlerdir.
ms.date: 10/14/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- metadata, extending
- attributes [.NET], metadata
- elements [.NET], attributes
- common language runtime, attributes
- annotating programming elements
- keyword-like descriptive declarations
- runtime, attributes
- extending metadata
ms.assetid: 30386922-1e00-4602-9ebf-526b271a8b87
ms.openlocfilehash: 9a83c0e8ee3476f43ccc2e88c21ccbbc0661bd19
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889224"
---
# <a name="extend-metadata-using-attributes"></a>Öznitelikleri kullanarak meta verileri genişletme

Ortak dil çalışma zamanı, türler, alanlar, Yöntemler ve özellikler gibi programlama öğelerine açıklama eklemek için öznitelikler olarak adlandırılan anahtar sözcük benzeri açıklayıcı bildirimler eklemenize olanak tanır. Çalışma zamanı için kodunuzu derlerken, Microsoft ara dili 'ne (MSIL) dönüştürülür ve derleyici tarafından oluşturulan meta verilerle birlikte taşınabilir bir çalıştırılabilir (PE) dosyası içine konur. Öznitelikleri, çalışma zamanı yansıma Hizmetleri kullanılarak ayıklanabilen meta verilere fazladan açıklayıcı bilgiler yerleştirmenizi sağlar. Derleyici, sınıfından türetilen özel sınıfların örneklerini bildirdiğinizde öznitelikler oluşturur <xref:System.Attribute?displayProperty=nameWithType> .

.NET çeşitli nedenlerle öznitelikler kullanır ve bir dizi sorunu ele almak için kullanılır. Öznitelikler, verilerin serileştirilmesi, güvenliği zorlamak için kullanılan özellikleri belirtmek ve tam zamanında (JıT) derleyicisine yönelik iyileştirmeleri sınırlamak için kodun kolayca hata ayıklaması gerektiğini anlatmaktadır. Öznitelikler Ayrıca, bir dosyanın veya kod yazarının adını kaydedebilir veya form geliştirme sırasında denetimlerin ve üyelerin görünürlüğünü denetleyebilir.

## <a name="related-articles"></a>İlgili makaleler:

|Başlık|Açıklama|
|-----------|-----------------|
|[Öznitelikleri Uygulama](applying-attributes.md)|Kodunuzun bir öğesine nasıl öznitelik uygulanacağını açıklar.|
|[Özel Öznitelikler Yazma](writing-custom-attributes.md)|Özel öznitelik sınıflarının nasıl tasarlanacağını açıklar.|
|[Özniteliklerde Depolanan Bilgileri Alma](retrieving-information-stored-in-attributes.md)|Yürütme bağlamına yüklenen kod için özel özniteliklerin nasıl alınacağını açıklar.|
|[Meta veriler ve Self-Describing bileşenleri](../metadata-and-self-describing-components.md)|Meta verilere genel bir bakış sağlar ve bir .NET taşınabilir yürütülebilir (PE) dosyasında nasıl uygulandığını açıklar.|
|[Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Özel öznitelik bilgilerinin yalnızca yansıma bağlamında nasıl alınacağını açıklar.|

## <a name="reference"></a>Başvuru

- <xref:System.Attribute?displayProperty=nameWithType>
