---
title: Tür Tasarımı Yönergeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: 2a3cca0139974cbc92ce85a19db73dfb3d13d1a0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743574"
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
 [Sınıf ve yapı](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md) [soyut sınıf tasarımı](../../../docs/standard/design-guidelines/abstract-class.md) arasında seçim yapma [statik sınıf tasarımı](../../../docs/standard/design-guidelines/static-class.md) [arabirim tasarım](../../../docs/standard/design-guidelines/interface.md) [yapı birimi](../../../docs/standard/design-guidelines/struct.md) tasarım [enum](../../../docs/standard/design-guidelines/enum.md) tasarım [iç içe türler](../../../docs/standard/design-guidelines/nested-types.md) *bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
