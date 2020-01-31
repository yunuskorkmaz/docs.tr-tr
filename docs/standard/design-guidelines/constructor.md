---
title: Oluşturucu Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
ms.openlocfilehash: 7ab795cd4c6e0ff5e1451c05987848c41bd69577
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741741"
---
# <a name="constructor-design"></a>Oluşturucu Tasarımı

İki tür Oluşturucu vardır: tür oluşturucular ve örnek oluşturucular.

Tür oluşturucuları statiktir ve tür kullanılmadan önce CLR tarafından çalıştırılır. Örnek oluşturucular, bir tür örneği oluşturulduğunda çalışır.

Tür oluşturucular hiçbir parametre alamaz. Örnek oluşturucular olabilir. Parametre kullanmayan örnek oluşturucular genellikle parametresiz oluşturucular olarak adlandırılır.

Oluşturucular, bir türün örneklerini oluşturmanın en doğal yoludur. Çoğu geliştirici, örnek oluşturma (örneğin, Factory yöntemleri) için alternatif yolları düşünmeleri için bir oluşturucuyu arar ve kullanmayı dener.

✔️ basit, ideal varsayılan oluşturucular sağlamayı düşünün.

Basit bir oluşturucunun çok az sayıda parametresi vardır ve tüm parametreler temel elemanlar veya Numaralandırmalar. Bu tür basit oluşturucular Framework kullanılabilirliğini artırır.

✔️, istenen işlemin semantiğini yeni bir örneğin yapıcıya doğrudan eşlenmiyorsa veya oluşturucunun tasarım yönergeleri doğal olarak yoksa, Oluşturucu yerine bir statik fabrika yöntemi kullanmayı düşünün.

✔️ Oluşturucu parametrelerini, ana özellikleri ayarlamak için kısayollar olarak kullanın.

Boş oluşturucuyu, ardından bazı özellik kümelerini ve birden çok bağımsız değişkenle bir oluşturucuyu kullanarak, semantik bir farklılık olmamalıdır.

✔️, Oluşturucu parametreleri için aynı adı ve Oluşturucu parametreleri özelliği ayarlamak için kullanılırsa özelliğini kullanın.

Bu parametre ve özellikler arasındaki tek fark büyük küçük harf olmalıdır.

✔️ oluşturucuda en az iş YAPıN.

Oluşturucular, Oluşturucu parametrelerini yakalamaya göre çok daha fazla çalışmamalıdır. Diğer bir işleme maliyeti, gerekli olana kadar Gecikmeli olmalıdır.

✔️, uygunsa örnek oluşturuculardan özel durumlar oluşturur.

Bu tür bir Oluşturucu gerekliyse, sınıflarda Ortak parametresiz oluşturucuyu açıkça bildirin ✔️.

Bir tür üzerinde açıkça herhangi bir Oluşturucu bildirmezseniz, birçok dil (gibi C#) otomatik olarak ortak parametresiz bir Oluşturucu ekler. (Soyut sınıflar korumalı bir Oluşturucu alır.)

Bir sınıfa parametreli Oluşturucu eklemek derleyicinin parametresiz oluşturucuyu eklemesini önler. Bu genellikle yanlışlıkla önemli değişikliklere neden olur.

❌ yapı birimlerinde açıkça parametresiz oluşturucular tanımlamayı ÖNLEYIN.

Bu, parametresiz Oluşturucu tanımlanmamışsa, dizideki her yuvada çalıştırılması gerekmediğinden, dizi oluşturmayı daha hızlı hale getirir. Birçok derleyicilerin C#, bu nedenle yapıların parametresiz oluşturuculara sahip olduğuna izin vermez.

❌ oluşturucusunun içindeki bir nesne üzerinde sanal üye çağırmaktan KAÇıNıN.

En türetilmiş türün Oluşturucusu henüz tam olarak çalıştırılmasa bile, sanal bir üyenin çağrılması en fazla türetilmiş geçersiz kılmanın çağrılmasına neden olur.

## <a name="type-constructor-guidelines"></a>Tür Oluşturucu yönergeleri

statik oluşturucuları özel hale getirmek ✔️.

Sınıf oluşturucusu olarak da adlandırılan statik bir Oluşturucu, bir türü başlatmak için kullanılır. CLR, türün ilk örneği oluşturulmadan veya bu türdeki herhangi bir statik üye çağrılmadan önce statik oluşturucuyu çağırır. Statik Oluşturucu çağrıldığında kullanıcının denetimi yoktur. Statik bir Oluşturucu özel değilse, CLR dışındaki kodla çağrılabilir. Oluşturucuda gerçekleştirilen işlemlere bağlı olarak, bu beklenmeyen davranışlara neden olabilir. C# Derleyici statik oluşturucuları özel olmaya zorlar.

❌ statik oluşturuculardan özel durumlar oluşturmaz.

Bir tür oluşturucusundan bir özel durum oluşturulursa, tür geçerli uygulama etki alanında kullanılamaz.

✔️, çalışma zamanı açıkça tanımlanmış bir statik oluşturucuya sahip olmayan türlerin performansını iyileştirebildiğinden, statik oluşturucuları açıkça kullanmak yerine, statik alanları satır içi olarak başlatmayı düşünün.

*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
