---
title: C# Diline ve.NET Framework'e Giriş
description: C# ve .NET'in temellerini öğrenin. C# dili ve .NET ekosistemi hakkında genel bir bakış alın.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 9feca97b141b08d418f6833374cbe3c7a0c26d66
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805779"
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>C# diline giriş ve .NET Çerçevesi

C#, geliştiricilerin .NET Framework üzerinde çalışan çeşitli güvenli ve sağlam uygulamalar oluşturmasına olanak tanıyan zarif ve tür emniyetli nesne yönelimli bir dildir. Windows istemci uygulamaları, XML Web hizmetleri, dağıtılmış bileşenler, istemci-sunucu uygulamaları, veritabanı uygulamaları ve çok daha fazlasını oluşturmak için C# kullanabilirsiniz. Visual C#gelişmiş bir kod düzenleyicisi, kullanışlı kullanıcı arabirimi tasarımcıları, tümleşik hata ayıklayıcı ve C# dili ve .NET Framework tabanlı uygulamalar geliştirmeyi kolaylaştırmak için diğer birçok araç sağlar.  
  
> [!NOTE]
> Visual C# dokümantasyonu, temel programlama kavramlarını anladığınızı varsayar. Tam bir acemi iseniz, Web'de bulunan Visual C# Express'i keşfetmek isteyebilirsiniz. Ayrıca pratik programlama becerilerini öğrenmek için C# ile ilgili kitaplardan ve Web kaynaklarından da yararlanabilirsiniz.  
  
## <a name="c-language"></a>C# dili

C# sözdizimi son derece anlamlı, ama aynı zamanda basit ve öğrenmesi kolay. C#'ın kıvırcık ayraç sözdizimi C, C++veya Java'yı bilen herkes tarafından anında tanınabilir. Bu dillerden herhangi birini bilen geliştiriciler genellikle kısa bir süre içinde C# alanında verimli bir şekilde çalışmaya başlayabilirler. C# sözdizimi C++'ın karmaşıklıklarının çoğunu basitleştirir ve nullable türleri, numaralandırmalar, temsilciler, lambda ifadeleri ve doğrudan bellek erişimi gibi güçlü özellikler sağlar. C#, artan tür güvenliği ve performansı sağlayan genel yöntemleri ve türleri ve koleksiyon sınıflarının uygulayıcılarının istemci koduyla kullanımı kolay özel yineleme davranışlarını tanımlamasını sağlayan yinelemeleri destekler. Dil-Tümleşik Sorgu (LINQ) ifadeleri, güçlü bir şekilde yazılan sorguyu birinci sınıf bir dil yapısı haline getirin.  
  
 Nesne yönelimli bir dil olarak C#, kapsülleme, kalıtım ve çok biçimlilik kavramlarını destekler. Yöntem, uygulamanın `Main` giriş noktası da dahil olmak üzere tüm değişkenler ve yöntemler sınıf tanımları içinde kapsüllenir. Bir sınıf doğrudan bir üst sınıftan devralınabilir, ancak herhangi bir sayıda arabirim uygulayabilir. Bir üst sınıftasanal yöntemleri geçersiz kılma `override` yöntemleri yanlışlıkla yeniden tanımlanmasını önlemek için bir yol olarak anahtar kelime gerektirir. C#'da, bir yapı hafif bir sınıf gibidir; arabirimleri uygulayabilen ancak devralmayı desteklemeyen yığın ayarı bir türdür.  
  
 Bu temel nesne yönelimli ilkelere ek olarak, C#, aşağıdakiler de dahil olmak üzere çeşitli yenilikçi dil yapıları aracılığıyla yazılım bileşenleri geliştirmeyi kolaylaştırır:  
  
- Tür güvenli olay bildirimleri etkinleştirmek *için temsilci*adı verilen kapsüllü yöntem imzaları.  
  
- Özel üye değişkenleri için erişimaracı olarak hizmet veren özellikler.  
  
- Çalışma zamanındaki türler hakkında bildirimsel meta veriler sağlayan öznitelikler.  
  
- Satır Satırlı XML dokümantasyon yorumları.  
  
- Çeşitli veri kaynaklarında yerleşik sorgu yetenekleri sağlayan Dil-Tümleşik Sorgu (LINQ).  
  
 COM nesneleri veya yerel Win32 DLL'ler gibi diğer Windows yazılımlarıyla etkileşimkurmanız gerekiyorsa, bunu "Interop" adı verilen bir işlem le C# ile yapabilirsiniz. Interop, C# programlarının yerel bir C++ uygulamasının yapabileceği hemen hemen her şeyi yapmasını sağlar. C#, doğrudan bellek erişiminin kritik olduğu durumlar için işaretçileri ve "güvenli olmayan" kod kavramını bile destekler.  
  
 C# oluşturma işlemi C ve C++ ile karşılaştırıldığında basittir ve Java'dakinden daha esnektir. Ayrı bir üstbilgi dosyası yoktur ve yöntem ve türlerin belirli bir sırada bildirilmesi şartı yoktur. C# kaynak dosyası herhangi bir sayıda sınıf, yapı, arabirim ve olay tanımlayabilir.  
  
 Ek C# kaynakları şunlardır:  
  
- Dile genel olarak iyi bir giriş için [C# Dil Belirtimi'nin](/dotnet/csharp/language-reference/language-specification/introduction)Bölüm 1'ine bakın.  
  
- C# dilinin belirli yönleri hakkında ayrıntılı bilgi için [C#](../language-reference/index.md)Referansı'na bakın.  
  
- LINQ hakkında daha fazla bilgi için [LINQ (Dil-Tümleşik Sorgu) adresine](../programming-guide/concepts/linq/index.md)bakın.  

## <a name="net-framework-platform-architecture"></a>.NET Çerçeve Platformu Mimarisi

 C# programları, Windows'un ortak dil çalışma zamanı (CLR) adı verilen sanal yürütme sistemi ve birleştirilmiş sınıf kitaplıkları kümesini içeren ayrılmaz bir bileşeni olan .NET Framework üzerinde çalışır. CLR, Microsoft tarafından, dillerin ve kitaplıkların sorunsuz bir şekilde birlikte çalıştığı yürütme ve geliştirme ortamları oluşturmak için temel oluşturan uluslararası bir standart olan ortak dil altyapısının (CLI) ticari uygulamasıdır.  
  
 C# ile yazılmış kaynak kodu, CLI belirtimine uygun bir [ara dil (IL)](../../standard/managed-code.md) olarak derlenir. Bit eşlemler ve dizeleri gibi IL kodu ve kaynakları, genellikle .exe veya .dll uzantılı olarak yürütülebilir bir dosyada depolanır. Derleme, derlemenin türleri, sürümü, kültürü ve güvenlik gereksinimleri hakkında bilgi sağlayan bir bildirim içerir.  
  
 C# programı yürütüldüğünde, derleme CLR'ye yüklenir ve bu da bildirimdeki bilgilere dayalı olarak çeşitli eylemlerde kalabilir. Daha sonra, güvenlik gereksinimleri karşılanırsa, CLR IL kodunu yerel makine yönergelerine dönüştürmek için Tam Zamanında (JIT) derleme gerçekleştirir. CLR ayrıca otomatik çöp toplama, özel durum işleme ve kaynak yönetimi yle ilgili diğer hizmetleri de sağlar. CLR tarafından yürütülen kod, belirli bir sistemi hedefleyen ana makine dilinde derlenen "yönetilmeyen kod" yerine bazen "yönetilen kod" olarak adlandırılır. Aşağıdaki diyagram, C# kaynak kod dosyalarının derleme zamanı ve çalışma zamanı ilişkilerini, .NET Framework sınıf kitaplıklarını, derlemeleri ve CLR'yi göstermektedir.  
  
 ![C# kaynak kodundan makine yürütmesine](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)  
  
 Dil birlikte çalışabilirliği .NET Framework'ün önemli bir özelliğidir. C# derleyicisi tarafından üretilen IL kodu Ortak Tür Belirtimine (CTS) uyduğundan, C#'dan oluşturulan IL kodu Visual Basic, Visual C++veya 20'den fazla CTS uyumlu dilin .NET sürümlerinden oluşturulan kodla etkileşim kurabilir. Tek bir derleme, farklı .NET dillerinde yazılmış birden çok modül içerebilir ve türler aynı dilde yazılmış gibi birbirlerine başvurabilirler.  
  
 .NET Framework, çalışma süresi hizmetlerine ek olarak, dosya girişi ve çıktısından dize işlemeye, XML ayrıştırma, Windows Forms denetimlerine kadar her şey için çok çeşitli yararlı işlevler sağlayan ad alanlarına ayrılmış 4000'den fazla sınıftan oluşan geniş bir kitaplık da içerir. Tipik C# uygulaması, ortak "sıhhi tesisat" işlerini işlemek için .NET Framework sınıf kitaplığını kapsamlı olarak kullanır.  
  
 .NET Framework hakkında daha fazla bilgi için [Microsoft .NET Framework'e Genel Bakış bölümüne](../../framework/get-started/overview.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görsel C ile Başlarken #](/visualstudio/ide/quickstart-csharp-console)
