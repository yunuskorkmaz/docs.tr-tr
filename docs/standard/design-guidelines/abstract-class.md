---
description: 'Daha fazla bilgi edinin: soyut sınıf tasarımı'
title: Soyut Sınıf Tasarımı
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: 5b1cd833bf43e5bf5731176243809393187e84d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642467"
---
# <a name="abstract-class-design"></a>Soyut Sınıf Tasarımı

❌ Soyut türlerde ortak veya korumalı iç oluşturucular tanımlamayın.

 Oluşturucular, yalnızca kullanıcıların türün örneklerini oluşturması gerekiyorsa genel olmalıdır. Soyut bir türün örneklerini oluşturamadığı için ortak Oluşturucusu olan bir soyut tür, kullanıcılar için yanlış tasarlanmış ve yanıltıcı olur.

 ✔️ soyut sınıflarda korumalı veya dahili bir oluşturucu tanımlar.

 Korunan bir Oluşturucu daha yaygındır ve yalnızca alt türler oluşturulduğunda temel sınıfın kendi başlatmasını yapmasına izin verir.

 Bir iç Oluşturucu, soyut sınıfın somut uygulamalarını sınıfı tanımlayan derlemeyle sınırlamak için kullanılabilir.

 ✔️, sevk ettiğiniz her soyut sınıftan devralan en az bir somut tür sağlar.

 Bunu yapmak, soyut sınıfın tasarımını doğrulamaya yardımcı olur. Örneğin,  <xref:System.IO.FileStream?displayProperty=nameWithType> <xref:System.IO.Stream?displayProperty=nameWithType> soyut sınıfın bir uygulamasıdır.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Tür tasarım yönergeleri](type.md)
- [Çerçeve tasarım yönergeleri](index.md)
