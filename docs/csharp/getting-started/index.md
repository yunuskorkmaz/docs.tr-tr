---
title: Kullanmaya başlayın-C# diline ve .NET 'e giriş "
description: C# ve .NET hakkında temel bilgileri öğrenin. C# diline ve .NET ekosistemine genel bakış alın.
ms.date: 10/13/2020
ms.openlocfilehash: 94d49be28fbdba8f58ca16e959a10643d6467c63
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160964"
---
# <a name="introduction-to-the-c-language-and-net"></a>C# diline ve .NET’e giriş

C#, şık ve tür açısından güvenli nesne yönelimli bir dildir. C#, geliştiricilerin .NET ekosisteminde çalışan çok sayıda güvenli ve güçlü uygulamalar oluşturmalarına olanak sağlar.

## <a name="c-language"></a>C# dili

C# sözdizimi büyük ölçüde ifade edilir, ancak kolayca öğrenilmesi ve kolay bir işlemdir. C# ' nin küme ayracı sözdizimi, C, C++, Java veya JavaScript 'e alışkın olan herkese anında tanınacaktır. Bu dillerden herhangi birini bilen geliştiriciler genellikle C# ' de kısa bir süre Içinde üretken bir şekilde çalışabilir. C# null yapılabilir türler, temsilciler, lambda ifadeleri, model eşleştirme ve güvenli doğrudan bellek erişimi gibi güçlü özellikler sağlar. C#, Artırılmış tür güvenliği ve performans sağlayan genel yöntemleri ve türleri destekler. C#, istemci kodu için özel davranışlar tanımlamak üzere koleksiyon sınıflarının uygulayıcıları 'nı etkinleştiren yineleyiciler sağlar. Language-Integrated Query (LINQ) ifadeleri, türü kesin belirlenmiş sorguyu birinci sınıf dil yapısına yapar.

C#, nesne yönelimli bir dil olarak kapsülleme, devralma ve çok biçimlilik kavramlarını destekler. Bir sınıf doğrudan bir üst sınıftan devralınabilir, ancak herhangi bir sayıda arabirim uygulayabilir. Bir üst sınıftaki sanal yöntemleri geçersiz kılan yöntemler, yanlışlıkla yeniden `override` tanımı önlemek için anahtar sözcüğünü gerektirir. C# ' de, bir struct basit bir sınıf gibidir; Bu, arabirimleri uygulayasağlayan ancak devralmayı desteklemeyen, yığın olarak ayrılmış bir türdür. C# Ayrıca, amacı Aslında veri değerlerini depolayan sınıf türleri olan kayıtlar da sağlar.

C#, aşağıdakiler de dahil olmak üzere çeşitli yenilikçi dil yapıları aracılığıyla yazılım bileşenleri geliştirmeyi kolaylaştırır:

- Tür kullanımı uyumlu olay bildirimlerini etkinleştiren *Temsilciler*adlı Kapsüllenmiş yöntem imzaları.
- Özel üye değişkenleri için erişimci işlevi sunan özellikler.
- Çalışma zamanında türler hakkında bildirime dayalı meta veriler sağlayan öznitelikler.
- Satır içi XML belge açıklamaları.
- Farklı türlerde veri kaynakları genelinde yerleşik sorgu özellikleri sağlayan Language-Integrated sorgu (LINQ).
- Veri türlerini ve değerlerini inceleyerek denetim akışına izin veren kalıp eşleme.

"Interop" adlı bir işlem aracılığıyla yerel bileşenlerle etkileşime geçebilirsiniz. Birlikte çalışma, C# programlarının yerel bir C++ uygulamasının gerçekleştirebildiği neredeyse her şeyi yapmasına olanak sağlar. C#, doğrudan bellek erişiminin kritik olduğu durumlar için işaretçileri ve "güvenli olmayan" kod kavramını destekler.

C# derleme işlemi, C ve C++ ile karşılaştırıldığında Java 'dan daha esnektir. Ayrı bir üst bilgi dosyası yoktur ve yöntemlerin ve türlerin belirli bir sırada bildirildiği hiçbir gereksinimi yoktur. C# kaynak dosyası herhangi bir sayıda sınıf, yapı, arabirim ve olay tanımlayabilir.

Ek C# kaynakları aşağıda verilmiştir:

- Dile yönelik iyi bir genel giriş için bkz. [C# turu](../tour-of-csharp/index.md).
- C# dilinin belirli yönleri hakkında ayrıntılı bilgi için bkz. [C# başvurusu](../language-reference/index.md).
- LINQ hakkında daha fazla bilgi için bkz. [LINQ (dil Ile tümleşik sorgu)](../programming-guide/concepts/linq/index.md).

## <a name="net-platform-architecture"></a>.NET platformu mimarisi

C# programları, ortak dil çalışma zamanı (CLR) ve birleştirilmiş bir sınıf kitaplıkları kümesi olarak adlandırılan bir sanal yürütme sistemi olan .NET üzerinde çalışır. CLR, uluslararası bir standart olan ortak dil altyapısının (CLı) Microsoft tarafından gerçekleştirilen ticari bir uygulama. CLı, dillerin ve kitaplıkların sorunsuz şekilde çalıştığı yürütme ve geliştirme ortamları oluşturmanın temelini oluşturur.

C# dilinde yazılan kaynak kodu, CLı belirtimine uyan bir [Ara dilde (IL)](../../standard/managed-code.md) derlenir. Il kodu ve bit eşlemler ve dizeler gibi kaynaklar, genellikle bir. dll uzantısıyla birlikte bir derlemede depolanır. Bütünleştirilmiş kod, derlemenin türleri, sürümü ve kültürü hakkında bilgi sağlayan bir bildirim içerir.

C# programı yürütüldüğünde, derleme CLR 'ye yüklenir. CLR, Il kodunu yerel makine yönergelerine dönüştürmek için tam zamanında (JıT) derleme gerçekleştirir. CLR, otomatik atık toplama, özel durum işleme ve kaynak yönetimiyle ilgili diğer hizmetleri sağlar. CLR tarafından yürütülen kod bazen "yönetilen kod" olarak adlandırılır ve bu, belirli bir sistemi hedefleyen yerel makine diline derlenen "yönetilmeyen kodun" aksine.

Dil birlikte çalışabilirliği, .NET 'in önemli bir özelliğidir. C# derleyicisi tarafından üretilen IL kodu ortak tür belirtimine (CTS) uygundur. C# ' den üretilen IL kodu, F #, Visual Basic, C++ veya 20 ' den fazla diğer CTS uyumlu dilin .NET sürümlerinden oluşturulan kodla etkileşime geçebilir. Tek bir derlemede, farklı .NET dillerinde yazılmış birden çok modül bulunabilir ve türler aynı dilde yazılmış gibi birbirlerine başvurabilir.

.NET çalışma zamanı hizmetlerine ek olarak kapsamlı kitaplıklar da içerir. Bu kitaplıklar birçok farklı iş yükünü destekler. Bunlar, dosya girişi ve çıktısından dize işlemeye kadar her şey için, Web uygulaması çerçevelerinden Windows Forms denetimlerine kadar çok çeşitli yararlı işlevler sunan ad alanları halinde düzenlenir. Tipik C# uygulaması, ortak "sıhhi tesisat" işlerini ele almak için .NET sınıf kitaplığını kapsamlı olarak kullanır.

.NET hakkında daha fazla bilgi için bkz. [.net 'e genel bakış](../../core/introduction.md).
