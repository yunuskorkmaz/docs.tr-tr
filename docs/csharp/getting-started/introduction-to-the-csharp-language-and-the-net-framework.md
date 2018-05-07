---
title: C# Diline ve.NET Framework'e Giriş
description: C# ve .NET temellerini öğrenin. C# dili ve .NET ekosistemi özetini alın.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: ab2d3042aff51e85b50296ce6f4382f588e1af71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>C# Diline ve.NET Framework'e Giriş
C# dildir ve geliştiricilerin çeşitli çalıştırmak güvenli ve sağlam uygulamalar oluşturmasına olanak sağlayan bir zarif ve tür kullanımı uyumlu nesne yönelimli [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Windows istemci uygulamaları, XML Web Hizmetleri, dağıtılmış bileşenler, istemci-sunucu uygulamalarını, veritabanı uygulamaları ve çok daha fazla oluşturmak için C# kullanabilirsiniz. Sağlayan Visual C# Gelişmiş kod düzenleyici, uygun kullanıcı arabirimi tasarımcıları, tümleşik hata ayıklayıcı ve diğer birçok Araçlar C# diline uygulama geliştirmeyi kolaylaştırmak için ve [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
> [!NOTE]
> Visual C# belge temel programlama kavramları bilgiye sahip olduğunuzu varsayar. Tam bir başlangıç varsa, Visual C# Express, Web'de kullanılabilir olduğu incelemek isteyebilirsiniz. Ayrıca books ve Web kaynaklar hakkında pratik programlama becerileri öğrenmek için C# yararlanabilirsiniz.  
  
## <a name="c-language"></a>C# Dili  
 C# sözdizimi yüksek oranda açıklayıcı henüz basit ve kolay öğrenmek de olabilir. C# ayracı sözdizimi C, C++ veya Java tanıdık bir kişiye anında tanınabilir olacaktır. Bu dillerden birinde bilen geliştiriciler genellikle üretken C# ' ta çok kısa bir süre içinde çalışmaya başlamak imkanınız olur. C# sözdizimi birçok C++ karmaşıklığını basitleştirir ve boş değer atanabilen değer türleri, numaralandırma, temsilciler, lambda ifadeleri ve gibi doğrudan bellek erişimi Java'da bulunmayan güçlü özellikler sağlar. C# genel yöntemler ve artan tür güvenliği ve performansı ve istemci kodu tarafından kullanılacak basit özel yineleme davranışları tanımlamak koleksiyon sınıflarının Implementers etkinleştirmek yineleyiciler sağlar türlerini destekler. [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] kesin türü belirtilmiş bir birinci sınıf dil yapısı sorgu ifadeleri olun.  
  
 Nesne yönelimli bir dil olarak C# kapsülleme, devralma ve çok biçimlilik kavramlarını destekler. Tüm değişkenleri ve yöntemleri dahil olmak üzere, `Main` yöntemi, uygulamanın giriş noktası, sınıf tanımları içine alınır. Bir sınıf doğrudan bir üst sınıftan alabilir, ancak herhangi bir sayıda arabirim uygulayabilir. Bir üst sınıf sanal yöntemleri geçersiz kılma yöntemleri gerektirir `override` anahtar sözcüğü yanlışlıkla yeniden tanımlama önlemek için bir yol olarak. C# ' ta yapı gibi hafif bir sınıf olduğunu; Bu arabirimleri uygulayabilir ancak devralmayı desteklemeyen bir yığın ayırma türüdür.  
  
 Bu temel nesne yönelimli ilkeler ek olarak, C#, aşağıdakiler de dahil olmak üzere çeşitli yenilikçi dil yapıları üzerinden yazılım bileşenleri geliştirmek kolaylaştırır:  
  
-   Adlı yöntem imzaları kapsüllenmiş *Temsilciler*, tür kullanımı uyumlu olay bildirimlerini etkinleştirin.  
  
-   Özel üye değişkenleri için erişimcileri olarak hizmet özellikleri.  
  
-   Çalışma zamanında türleri hakkında bildirim temelli meta veri sağlayan öznitelikler.  
  
-   Satır içi XML belge açıklamaları.  
  
-   [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] çeşitli veri kaynakları arasında yerleşik sorgu yetenekleri sağlar.  
  
 COM nesneleri veya yerel Win32 DLL'leri gibi diğer Windows yazılım ile etkileşim kurmak varsa, C# ' ta "Birlikte çalışabilirliği." adlı bir işlem bunu yapabilirsiniz Birlikte çalışma neredeyse her şeyi, yerel C++ uygulaması yapabileceği yapmak C# programları sağlar. C# bile işaretçileri ve "güvenli olmayan" kod kavramını doğrudan bellek erişimi kesinlikle kritik olduğu durumlarda destekler.  
  
 C# derleme basit bir işlemdir C ve C++ karşılaştırıldığında ve Java olduğundan daha esnektir. Hiçbir ayrı üstbilgi dosyaları ve yöntemleri ve türleri belirli bir sırada bildirilmesi gereksinimi vardır. C# kaynak dosyasını, sınıflar, yapılar, arabirimleri ile olaylarını herhangi bir sayıda tanımlayabilir.  
  
 Ek C# kaynakları şunlardır:  
  
-   Dil ilişkin iyi genel giriş için bkz: Bölüm 1 / [C# dil belirtimi](../../csharp/language-reference/language-specification/index.md).  
  
-   C# dili belirli yönleri hakkında ayrıntılı bilgi için bkz: [C# başvurusu](../../csharp/language-reference/index.md).  
  
-   Hakkında daha fazla bilgi için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], bkz: [LINQ (dil ile tümleşik sorgu)](../programming-guide/concepts/linq/index.md).  

## <a name="net-framework-platform-architecture"></a>.NET framework Platform mimarisi  
 C# programları çalıştırmak [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], sanal bir yürütme sistemi içeren bir Windows vazgeçilmez bir bileşenidir ortak dil çalışma zamanı (CLR) ve sınıf kitaplıkları birleştirilmiş bir dizi olarak adlandırılır. CLR ticari Microsoft tarafından ortak dil altyapısı (CLI), yürütme ve diller ve kitaplıkları birlikte sorunsuz çalıştığı geliştirme ortamları oluşturmak için temel bir uluslararası standart uygulamasıdır.  
  
 C# ile yazılmış kaynak kodu CLI belirtimine uygun bir ara dile (IL) derlenir. Bit eşlemler ve dizeler gibi kaynakları ve IL kodu genellikle .exe veya .dll uzantısına sahip bir derleme adlı yürütülebilir bir dosyanın disk üzerinde depolanır. Bir derlemeyi derlemenin türleri, sürüm, kültür ve güvenlik gereksinimleri hakkında bilgi sağlayan bir bildirimi içerir.  
  
 C# programı yürütüldüğünde derleme bildirimdeki bilgilere göre çeşitli eylemler sürebilir CLR içine yüklenir. Ardından, güvenlik gereksinimlerin karşılanması durumunda CLR IL kodu yerel makine yönergelerine dönüştürmek için tam zamanında (JIT) derleme gerçekleştirir. CLR ayrıca diğer hizmetler ile ilgili otomatik çöp toplama, özel durum işleme ve kaynak yönetimi sağlar. CLR tarafından yürütülen kod bazen "yönetilen kod" aksine "belirli bir sistemi hedefleyen yerel makine diline derlenmiş yönetilmeyen kod" denir. Aşağıdaki diyagram, C# kaynak kodu dosyaları, .NET Framework sınıf kitaplıkları, derlemeler ve CLR derleme zamanı ve çalışma zamanı ilişkilerini gösterir.  
  
 ![C&#35; kaynak makine yürütme için kodu](../../csharp/getting-started/media/netarchitecture.png "NETarchitecture")  
  
 Diller arası birlikte çalışabilirlik özelliğidir anahtar [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. C# Derleyici tarafından üretilen IL kodu ortak tür belirtimi (CTS) uyumlu olmadığından, C# ' den oluşturulan IL kodu Visual Basic, Visual C++ veya 20'den fazla CTS uyumlu dillerinden biri .NET sürümlerinden oluşturulan kod ile etkileşim kurabilirsiniz. Tek bir derleme farklı .NET dilinde yazılmış birçok modül içerebilir ve yalnızca aynı dilde yazılmış sanki türleri birbirine başvuruda bulunabilir.  
  
 Çalıştırma zamanı hizmetlerine ek olarak [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] de sağlayan çok çeşitli yararlı işlevselliği için her şeyi dosya giriş ve çıkış XML dize düzenlemesi için ad alanları halinde düzenlenmiş 4000 sınıfların kapsamlı bir kitaplık içerir , Windows Forms denetimlerine ayrıştırma. Tipik C# uygulamanın kullandığı [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] yaygın ortak "tesisatı" işlerinden işlemek için sınıf kitaplığı.  
  
 .NET Framework hakkında daha fazla bilgi için bkz: [Microsoft .NET Framework genel bakış](../../framework/get-started/overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C#](../../csharp/index.md) [Visual C# ve Visual Basic'e Başlarken](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
