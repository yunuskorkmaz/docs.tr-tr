---
title: Soyut Sınıf Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: e6a5923f293ed536fb272f6fe6c805067aede0ab
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280783"
---
# <a name="abstract-class-design"></a>Soyut Sınıf Tasarımı

❌Soyut türlerde ortak veya korumalı iç oluşturucular tanımlamayın.

 Oluşturucular, yalnızca kullanıcıların türün örneklerini oluşturması gerekiyorsa genel olmalıdır. Soyut bir türün örneklerini oluşturamadığı için ortak Oluşturucusu olan bir soyut tür, kullanıcılar için yanlış tasarlanmış ve yanıltıcı olur.

 ✔️ soyut sınıflarda korumalı veya dahili bir oluşturucu tanımlar.

 Korunan bir Oluşturucu daha yaygındır ve yalnızca alt türler oluşturulduğunda temel sınıfın kendi başlatmasını yapmasına izin verir.

 Bir iç Oluşturucu, soyut sınıfın somut uygulamalarını sınıfı tanımlayan derlemeyle sınırlamak için kullanılabilir.

 ✔️, sevk ettiğiniz her soyut sınıftan devralan en az bir somut tür sağlar.

 Bunu yapmak, soyut sınıfın tasarımını doğrulamaya yardımcı olur. Örneğin, <xref:System.IO.FileStream?displayProperty=nameWithType> <xref:System.IO.Stream?displayProperty=nameWithType> soyut sınıfın bir uygulamasıdır.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Tür tasarım yönergeleri](type.md)
- [Çerçeve tasarım yönergeleri](index.md)
