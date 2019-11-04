---
title: C# Diline ve.NET Framework'e Giriş
description: C# Ve .net temelleri hakkında bilgi edinin. C# Dile ve .net ekosistemine genel bakış alın.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 57fd4ab59a1162145087b375cbbb71816a10e78c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420333"
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>C# Diline ve.NET Framework'e Giriş

C#, geliştiricilerin .NET Framework çalışan çeşitli güvenli ve güçlü uygulamalar oluşturmalarına olanak tanıyan, şık ve tür açısından güvenli bir nesne yönelimli dildir. Windows istemci uygulamaları C# , XML Web Hizmetleri, dağıtılmış bileşenler, istemci-sunucu uygulamaları, veritabanı uygulamaları ve çok daha fazlasını oluşturmak için kullanabilirsiniz. Visual C# , gelişmiş bir kod düzenleyici, uygun Kullanıcı arabirimi tasarımcıları, tümleşik hata ayıklayıcı ve C# dile ve .NET Framework göre uygulama geliştirmeyi kolaylaştırmak için birçok diğer araç sağlar.  
  
> [!NOTE]
> Görsel C# belgeler, temel programlama kavramlarını anladığınızı varsayar. Yeni bir başlangıç yapıyorsanız, Web 'de bulunan Visual C# Express 'i incelemek isteyebilirsiniz. Ayrıca, pratik programlama becerileri öğrenmek C# için kitaplar ve Web kaynaklarından yararlanabilirsiniz.  
  
## <a name="c-language"></a>C# Dili

 C#sözdizimi büyük ölçüde ifade edilir, ancak kolayca öğrenilmesi ve kolay bir işlemdir. Küme ayracı sözdizimi C# , C C++ veya Java 'yı bilen herkese anında tanınacaktır. Bu dillerden herhangi birini bilen geliştiriciler genellikle çok kısa bir süre C# içinde üretken bir şekilde çalışmaya başlayabilirler. C#sözdizimi, C++ ' nin birçok karmaşıklıklarını basitleştirir ve null yapılabilir değer türleri, numaralandırmalar, temsilciler, lambda ifadeleri ve doğrudan bellek erişimi gibi Java 'da bulunmayan güçlü özellikler sağlar. C#, Artırılmış tür güvenliği ve performans ve yineleyiciler sağlayan genel yöntemleri ve türleri destekler ve bu sayede, istemci kodu tarafından kullanılması kolay olan özel yineleme davranışları tanımlamak için koleksiyon sınıflarının uygulayıcıları özelliğini etkinleştirir. [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] ifadeler, türü kesin belirlenmiş sorguyu birinci sınıf dil yapısına getirir.  
  
 Nesne yönelimli bir dil olarak kapsülleme, C# devralma ve çok biçimlilik kavramlarını destekler. `Main` yöntemi dahil olmak üzere tüm değişkenler ve Yöntemler, uygulamanın giriş noktası, sınıf tanımları içinde kapsüllenir. Bir sınıf doğrudan bir üst sınıftan devralınabilir, ancak herhangi bir sayıda arabirim uygulayabilir. Bir üst sınıftaki sanal yöntemleri geçersiz kılan yöntemler, yanlışlıkla yeniden tanımlama önlemek için `override` anahtar sözcüğünü gerektirir. ' C#De, bir yapı hafif bir sınıf gibidir; arabirim uygulayan, ancak devralmayı desteklemeyen, yığın olarak ayrılmış bir türdür.  
  
 Bu temel nesne odaklı ilkelere ek olarak, C# aşağıdakiler de dahil olmak üzere çeşitli yenilikçi dil yapıları aracılığıyla yazılım bileşenleri geliştirmeyi kolaylaştırır:  
  
- Tür kullanımı uyumlu olay bildirimlerini etkinleştiren *Temsilciler*adlı Kapsüllenmiş yöntem imzaları.  
  
- Özel üye değişkenleri için erişimci işlevi sunan özellikler.  
  
- Çalışma zamanında türler hakkında bildirime dayalı meta veriler sağlayan öznitelikler.  
  
- Satır içi XML belge açıklamaları.  
  
- çeşitli veri kaynakları genelinde yerleşik sorgu özellikleri sağlayan [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].  
  
 COM nesneleri veya yerel Win32 DLL 'Leri gibi diğer Windows yazılımlarıyla etkileşimde bulunmak istiyorsanız bunu "birlikte çalışma" adlı bir işlem C# aracılığıyla yapabilirsiniz. Birlikte çalışabilirlik C# , programların bir yerel C++ uygulamanın yapabildiği neredeyse her şeyi yapmasına olanak sağlar. C#, doğrudan bellek erişiminin kesinlikle kritik olduğu durumlar için işaretçileri ve "güvenli olmayan" kod kavramını destekler.  
  
 Yapı C# Işlemi, Java 'dan daha fazla C ve C++ daha esnek ile karşılaştırılır. Ayrı bir üst bilgi dosyası yoktur ve yöntemlerin ve türlerin belirli bir sırada bildirildiği hiçbir gereksinimi yoktur. C# Kaynak dosya herhangi bir sayıda sınıf, yapı, arabirim ve olay tanımlayabilir.  
  
 Ek C# kaynaklar aşağıda verilmiştir:  
  
- Dile yönelik iyi bir genel giriş için, bkz. [ C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction)Bölüm 1.  
  
- C# Dilin belirli yönleri hakkında ayrıntılı bilgi için bkz. [ C# başvuru](../language-reference/index.md).  
  
- [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]hakkında daha fazla bilgi için bkz. [LINQ (dil Ile tümleşik sorgu)](../programming-guide/concepts/linq/index.md).  

## <a name="net-framework-platform-architecture"></a>.NET Framework platform mimarisi

 C#Programlar, ortak dil çalışma zamanı (CLR) ve Birleşik sınıf kitaplıkları kümesi adlı bir sanal yürütme sistemi içeren, Windows 'un integral bir bileşeni olan .NET Framework çalışır. CLR, dil ve kitaplıkların sorunsuz şekilde çalıştığı yürütme ve geliştirme ortamları oluşturmaya yönelik temel bir uluslararası standart olan ortak dil altyapısının (CLı) Microsoft tarafından oluşturulan ticari bir uygulamasıdır.  
  
 İçinde C# yazılan kaynak kodu, CLI belirtimine uyan bir [Ara dilde (IL)](../../standard/managed-code.md) derlenir. Il kodu ve bit eşlemler ve dizeler gibi kaynaklar, genellikle bir. exe veya. dll uzantısıyla derleme adlı yürütülebilir bir dosyada diskte depolanır. Bütünleştirilmiş kod, derlemenin türleri, sürümü, kültürü ve güvenlik gereksinimleri hakkında bilgi sağlayan bir bildirim içerir.  
  
 C# Program yürütüldüğünde, derleme clr 'ye yüklenir ve bu, bildirimdeki bilgilere bağlı olarak çeşitli eylemler gerçekleştirebilir. Daha sonra, güvenlik gereksinimleri karşılanırsa, Il kodunu yerel makine yönergelerine dönüştürmek için CLR tam zamanında (JıT) derleme gerçekleştirir. CLR Ayrıca otomatik çöp toplama, özel durum işleme ve kaynak yönetimiyle ilgili diğer hizmetleri de sağlar. CLR tarafından yürütülen kod bazen "yönetilen kod" olarak adlandırılır. Bu, belirli bir sistemi hedefleyen yerel makine dilinde derlenen "yönetilmeyen kodun" aksine. Aşağıdaki diyagramda C# kaynak kodu dosyalarının derleme zamanı ve çalışma zamanı ilişkileri, .NET Framework sınıf kitaplıkları, derlemeler ve clr gösterilmektedir.  
  
 ![C&#35; kaynak kodundan makine yürütmeye](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)  
  
 Dil birlikte çalışabilirliği, .NET Framework temel bir özelliğidir. C# Derleyici tarafından üretilen IL kodu ortak tür BELIRTIMINE (Cts) uygun olduğundan, ÖĞESINDEN C# oluşturulan IL kodu Visual Basic, görselin C++.net sürümlerinden veya 20 ' den daha fazlası tarafından oluşturulan kodla etkileşime girebilirler CTS uyumlu diller. Tek bir derleme, farklı .NET dillerinde yazılmış birden çok modül içerebilir ve türler aynı dilde yazıldıklarında olduğu gibi birbirlerine başvurabilir.  
  
 Çalışma zamanı hizmetlerine ek olarak .NET Framework, dosya girişi ve çıktısından dize işlemeye XML 'e kadar her şey için çok çeşitli yararlı işlevler sağlayan ad alanları halinde düzenlenmiş 4000 ' den fazla sınıftan oluşan kapsamlı bir kitaplık içerir. Windows Forms denetimleri için ayrıştırma. Tipik C# uygulama, ortak "sıhhi tesisat" kullanımlarını işlemek için .NET Framework sınıf kitaplığını kapsamlı şekilde kullanır.  
  
 .NET Framework hakkında daha fazla bilgi için bkz. [Microsoft .NET Framework 'e genel bakış](../../framework/get-started/overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#](../index.md)
- [Görsele BaşlarkenC#](/visualstudio/ide/quickstart-csharp-console)
