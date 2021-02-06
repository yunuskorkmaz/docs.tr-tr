---
description: 'Hakkında daha fazla bilgi edinin: tür tasarım yönergeleri'
title: Tür Tasarımı Yönergeleri
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: d2c193d41dda118558cc5e7541f7e2dfbaf1a369
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641843"
---
# <a name="type-design-guidelines"></a>Tür Tasarımı Yönergeleri

CLR perspektifinden, türlerin yalnızca iki kategorisi vardır: başvuru türleri ve değer türleri, ancak çerçeve tasarımı hakkında bir tartışma amacıyla, türleri, her biri kendi belirli tasarım kurallarına sahip daha fazla mantıksal gruba böyoruz.

 Sınıflar, başvuru türlerinin genel durumdur. Bu kişiler, çerçevelerin çoğunluğunda türlerin toplu olarak kullanılabilmesini sağlarlar. Sınıflar, destekledikleri ve genel uygulanabilirliği olan zengin nesne yönelimli özellikler kümesi için popülerliğini borçlar. Taban Sınıflar ve soyut sınıflar, genişletilebilirlik ile ilgili özel mantıksal gruplardır.

 Arabirimler, başvuru türleri ve değer türleri tarafından uygulanabilen türlerdir. Bunlar, bu nedenle, polimorfik, başvuru türleri ve değer türleri için kökler olarak işlev görebilir. Ayrıca, arabirimler, CLR tarafından yerel olarak desteklenmeyen birden çok devralmanın benzetimini yapmak için de kullanılabilir.

 Yapılar, değer türlerinin genel durumdur ve dil temel elemanlarına benzer küçük, basit türler için ayrılmalıdır.

 Numaralandırmalar, haftanın günleri, konsol renkleri vb. gibi kısa değer kümelerini tanımlamak için kullanılan değer türlerinin özel bir durumdur.

 Statik sınıflar, statik üyeler için kapsayıcılar olması amaçlanan türlerdir. Bunlar genellikle diğer işlemlere kısayollar sağlamak için kullanılır.

 Temsilciler, özel durumlar, öznitelikler, diziler ve koleksiyonlar, belirli kullanımlar için tasarlanan başvuru türlerinin tüm özel durumlarıyla ve tasarım ve kullanımlarıyla ilgili yönergelerin bu kitapta başka bir yerde ele alınmıştır.

 ✔️ Her türün iyi tanımlanmış bir ilgili üye kümesi olduğundan emin olmak için, yalnızca, ilişkisiz işlevlerin rastgele bir koleksiyonunu değil.

## <a name="in-this-section"></a>Bu Bölümde

 [Sınıf ve yapı](choosing-between-class-and-struct.md) [soyut sınıf tasarımı](abstract-class.md) arasında seçim yapma [statik sınıf tasarımı](static-class.md) [arabirim tasarım](interface.md) [yapı birimi](struct.md) tasarım [enum](enum.md) tasarım [iç içe türler](nested-types.md) *bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
