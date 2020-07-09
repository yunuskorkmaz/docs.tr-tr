---
title: C# Diline ve.NET Framework'e Giriş
description: C# ve .NET hakkında temel bilgileri öğrenin. C# diline ve .NET ekosistemine genel bakış alın.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 55b90d10a1d8ac8534ba98e1cc5af906d69822a6
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100840"
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>C# diline ve .NET Framework giriş

C#, geliştiricilerin .NET ekosisteminde çalışan çok sayıda güvenli ve güçlü uygulamalar oluşturmalarına olanak tanıyan, şık ve tür açısından güvenli bir nesne yönelimli dildir. .Net ekosistemi, .net [Core](../../core/index.yml)ile sınırlı olmamak üzere tüm .net uygulamalarından oluşur ve [.NET Framework](../../framework/index.yml). Bu makale .NET Framework odaklanır. Windows istemci uygulamaları, XML Web Hizmetleri, dağıtılmış bileşenler, istemci-sunucu uygulamaları, veritabanı uygulamaları ve çok daha fazlasını oluşturmak Için C# kullanabilirsiniz.

> [!NOTE]
> Visual C# belgeleri, temel programlama kavramlarını anladığınızı varsayar. Yeni bir başlangıç yapıyorsanız, Web 'de bulunan Visual C# Express 'i incelemek isteyebilirsiniz. Pratik programlama becerileri öğrenmek Için C# hakkındaki kitaplar ve Web kaynaklarından de yararlanabilirsiniz.

## <a name="c-language"></a>C# dili

C# sözdizimi büyük ölçüde ifade edilir, ancak kolayca öğrenilmesi ve kolay bir işlemdir. C# ' nin küme ayracı sözdizimi, C, C++ veya Java 'yı bilen herkese anında tanınacaktır. Bu dillerden herhangi birini bilen geliştiriciler genellikle C# ' de kısa bir süre Içinde üretken bir şekilde çalışmaya başlayabilirler. C# sözdizimi C++ ' ın birçok karmaşıklıklarını basitleştirir ve null yapılabilir türler, numaralandırmalar, temsilciler, lambda ifadeleri ve doğrudan bellek erişimi gibi güçlü özellikler sağlar. C#, daha yüksek tür güvenliği ve performans ve yineleyiciler sağlayan genel yöntemleri ve türleri destekler. Bu, koleksiyon sınıflarının ımplemenonun istemci kodu tarafından kullanılması kolay özel yineleme davranışları tanımlamasına olanak tanır. Dil ile tümleşik sorgu (LINQ) ifadeleri, türü kesin belirlenmiş sorguyu birinci sınıf dil yapısına yapar.

C#, nesne yönelimli bir dil olarak kapsülleme, devralma ve çok biçimlilik kavramlarını destekler. Yöntemi dahil olmak üzere tüm değişkenler ve Yöntemler, `Main` uygulamanın giriş noktası, sınıf tanımları içinde kapsüllenir. Bir sınıf doğrudan bir üst sınıftan devralınabilir, ancak herhangi bir sayıda arabirim uygulayabilir. Bir üst sınıftaki sanal yöntemleri geçersiz kılan yöntemler, yanlışlıkla yeniden `override` tanımı önlemek için anahtar sözcüğünü gerektirir. C# ' de, bir struct basit bir sınıf gibidir; arabirim uygulayan, ancak devralmayı desteklemeyen, yığın olarak ayrılmış bir türdür.

C#, bu temel nesne odaklı ilkelere ek olarak, aşağıdakiler de dahil olmak üzere çeşitli yenilikçi dil yapıları aracılığıyla yazılım bileşenleri geliştirmeyi kolaylaştırır:

- Tür kullanımı uyumlu olay bildirimlerini etkinleştiren *Temsilciler*adlı Kapsüllenmiş yöntem imzaları.
- Özel üye değişkenleri için erişimci işlevi sunan özellikler.
- Çalışma zamanında türler hakkında bildirime dayalı meta veriler sağlayan öznitelikler.
- Satır içi XML belge açıklamaları.
- Çeşitli veri kaynakları genelinde yerleşik sorgu özellikleri sağlayan, dil ile tümleşik sorgu (LINQ).

COM nesneleri veya yerel Win32 DLL 'Leri gibi diğer Windows yazılımlarıyla etkileşimde bulunmak istiyorsanız bunu "birlikte çalışma" adlı bir işlem aracılığıyla C# içinde yapabilirsiniz. Birlikte çalışma, C# programlarının yerel bir C++ uygulamasının gerçekleştirebildiği neredeyse her şeyi yapmasına olanak sağlar. C#, doğrudan bellek erişiminin kritik olduğu durumlar için işaretçileri ve "güvenli olmayan" kod kavramını destekler.

C# derleme işlemi, C ve C++ ile karşılaştırıldığında Java 'dan daha esnektir. Ayrı bir üst bilgi dosyası yoktur ve yöntemlerin ve türlerin belirli bir sırada bildirildiği hiçbir gereksinimi yoktur. C# kaynak dosyası herhangi bir sayıda sınıf, yapı, arabirim ve olay tanımlayabilir.

Ek C# kaynakları aşağıda verilmiştir:

- Dile yönelik iyi bir genel giriş için, bkz. [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction)Bölüm 1.
- C# dilinin belirli yönleri hakkında ayrıntılı bilgi için bkz. [C# başvurusu](../language-reference/index.md).
- LINQ hakkında daha fazla bilgi için bkz. [LINQ (dil Ile tümleşik sorgu)](../programming-guide/concepts/linq/index.md).

## <a name="net-framework-platform-architecture"></a>.NET Framework platform mimarisi

C# programları, ortak dil çalışma zamanı (CLR) ve birleştirilmiş bir sınıf kitaplıkları kümesi adlı bir sanal yürütme sistemi içeren, Windows 'un integral bir bileşeni olan .NET Framework çalışır. CLR, dil ve kitaplıkların sorunsuz şekilde çalıştığı yürütme ve geliştirme ortamları oluşturmaya yönelik temel bir uluslararası standart olan ortak dil altyapısının (CLı) Microsoft tarafından oluşturulan ticari bir uygulamasıdır.

C# dilinde yazılan kaynak kodu, CLı belirtimine uyan bir [Ara dilde (IL)](../../standard/managed-code.md) derlenir. Il kodu ve bit eşlemler ve dizeler gibi kaynaklar, genellikle bir. exe veya. dll uzantısıyla derleme adlı yürütülebilir bir dosyada diskte depolanır. Bütünleştirilmiş kod, derlemenin türleri, sürümü, kültürü ve güvenlik gereksinimleri hakkında bilgi sağlayan bir bildirim içerir.

C# programı yürütüldüğünde, derleme CLR 'ye yüklenir ve bu, bildirimdeki bilgilere bağlı olarak çeşitli eylemler gerçekleştirebilir. Daha sonra, güvenlik gereksinimleri karşılanıyorsa, CLR tam zamanında (JıT) derleme gerçekleştirerek Il kodunu yerel makine yönergelerine dönüştürür. CLR Ayrıca otomatik çöp toplama, özel durum işleme ve kaynak yönetimiyle ilgili diğer hizmetleri de sağlar. CLR tarafından yürütülen kod bazen "yönetilen kod" olarak adlandırılır ve bu, belirli bir sistemi hedefleyen yerel makine diline derlenen "yönetilmeyen kodun" aksine. Aşağıdaki diyagramda C# kaynak kodu dosyalarının derleme zamanı ve çalışma zamanı ilişkileri, .NET Framework sınıf kitaplıkları, derlemeler ve CLR gösterilmektedir.

![C# kaynak kodundan makine yürütmeye](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)

Dil birlikte çalışabilirliği, .NET Framework temel bir özelliğidir. C# derleyicisi tarafından üretilen IL kodu ortak tür belirtimine (CTS) uygun olduğundan, C# ' dan oluşturulan IL kodu, Visual Basic, Visual C++ veya 20 ' den fazla diğer CTS uyumlu dilden oluşan .NET sürümlerinden oluşturulan kodla etkileşime geçebilir. Tek bir derlemede, farklı .NET dillerinde yazılmış birden çok modül bulunabilir ve türler aynı dilde yazılmış gibi birbirlerine başvurabilir.

Çalışma zamanı hizmetlerine ek olarak .NET Framework, dosya girişi ve çıktısından dize işlemeye kadar her şey için, Windows Forms denetimlere kadar çok çeşitli yararlı işlevler sağlayan ad alanları halinde düzenlenmiş kapsamlı 4000 sınıftan oluşan kapsamlı bir kitaplık içerir. Tipik C# uygulaması, ortak "sıhhi tesisat" seçeneklerini işlemek için .NET Framework sınıf kitaplığını kapsamlı olarak kullanır.

.NET Framework hakkında daha fazla bilgi için bkz. [Microsoft .NET Framework 'e genel bakış](../../framework/get-started/overview.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual C ile çalışmaya başlama #](/visualstudio/ide/quickstart-csharp-console)
