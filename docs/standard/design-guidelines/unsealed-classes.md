---
title: Mühürsüz Sınıflar
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 6804a79e8beee1d42e313509966b46239e66c25f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743557"
---
# <a name="unsealed-classes"></a>Mühürsüz Sınıflar
Korumalı sınıflar öğesinden devralınamaz ve genişletilebilirliği engeller. Buna karşılık, öğesinden devralınılabilecek sınıflar korumasız sınıflar olarak adlandırılır.

 ✔️, bir çerçeveye pahalı ve çok daha fazla bir genişletilebilirlik sağlamak için, eklenmiş bir sanal veya korumalı üye olmadan korumasız sınıflar kullanmayı düşünün.

 Geliştiriciler, özel oluşturucular, yeni yöntemler veya yöntem aşırı yüklemeleri gibi kolay Üyeler eklemek için genellikle korumasız sınıflardan devralması ister. Örneğin, `System.Messaging.MessageQueue` korumasız olur ve bu sayede kullanıcıların belirli bir sıra yolu için varsayılan olarak özel kuyruklar oluşturmalarına veya belirli senaryolar için API 'YI basitleştiren özel yöntemler eklemesine olanak tanır.

 Sınıflar çoğu programlama dilinde varsayılan olarak korumasız olur ve çerçeveler içindeki çoğu sınıf için de önerilen varsayılan değer budur. Korumasız türler tarafından sağlanan genişletilebilirlik, çatı kullanıcıları tarafından çok daha fazla teşekkürler ve korumasız türlerle ilişkili görece düşük test maliyetlerinden dolayı sağlanması oldukça ucuzdur.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Mühürleme](../../../docs/standard/design-guidelines/sealing.md)
