---
description: 'Daha fazla bilgi edinin: statik sınıf tasarımı'
title: Statik Sınıf Tasarımı
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: 16db470ab0975a5545617c9c5471d6ac157e688b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782474"
---
# <a name="static-class-design"></a>Statik Sınıf Tasarımı

Statik bir sınıf, yalnızca statik Üyeler ( <xref:System.Object?displayProperty=nameWithType> ve büyük olasılıkla özel bir Oluşturucu) içeren bir sınıf olarak tanımlanır. Bazı diller statik sınıflar için yerleşik destek sağlar. C# 2,0 ve üzeri sürümlerde, bir sınıf statik olarak bildirildiğinde, mühürlenmiş, soyut ve herhangi bir örnek üyesi geçersiz kılınmaz veya bildirilebilecek.

 Statik sınıflar saf nesne odaklı tasarım ve basitlik arasında bir uzlaşdır. Bunlar genellikle diğer işlemlere (gibi) kısayollar sağlamak için kullanılır (örneğin <xref:System.IO.File?displayProperty=nameWithType> ), uzantı yöntemlerinin sahipleri veya tam bir nesne odaklı sarmalayıcının izin verilmeyen bir sarmalayıcı (gibi <xref:System.Environment?displayProperty=nameWithType> ).

 ✔️ statik sınıfları gelişigüzel bir şekilde kullanın.

 Statik sınıflar yalnızca çerçevenin nesne odaklı çekirdeği için destekleme sınıfları olarak kullanılmalıdır.

 ❌ Statik sınıfları çeşitli demet olarak değerlendirin.

 ❌ Statik sınıflarda örnek üyelerini bildirme veya geçersiz kılma.

 ✔️ statik sınıfları korumalı, soyut olarak bildirir ve programlama dilinizin statik sınıflar için yerleşik desteği yoksa özel bir örnek oluşturucu ekleyin.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Tür tasarım yönergeleri](type.md)
- [Çerçeve tasarım yönergeleri](index.md)
