---
title: .NET Framework Şifreleme Modeli
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ced7ed2cb8d3ae3bb24211c6e7dafd1744fb9559
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587462"
---
# <a name="net-framework-cryptography-model"></a>.NET Framework Şifreleme Modeli
.NET Framework standart birçok şifreleme algoritması uygulamaları sağlar. Bu algoritmalar kullanın ve güvenli olası varsayılan özelliklere sahip kolaydır. Ayrıca, .NET Framework şifreleme modeli nesne devralma, akış tasarım ve yapılandırma son derece genişletilebilir.  
  
## <a name="object-inheritance"></a>Nesne Devralma  
 .NET Framework güvenlik sistemi, Genişletilebilir bir türetilmiş sınıf devralma deseni uygular. Hiyerarşi aşağıdaki gibidir:  
  
-   Algoritma türü sınıfı, gibi <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> veya <xref:System.Security.Cryptography.HashAlgorithm>. Bu düzey soyuttur.  
  
-   Bir algoritma türü sınıfından devralan algoritma sınıfı; Örneğin, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, veya <xref:System.Security.Cryptography.ECDiffieHellman>. Bu düzey soyuttur.  
  
-   Bir algoritma sınıfından devralan bir algoritma sınıfı uyarlamasını; Örneğin, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, veya <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Bu düzey tam olarak uygulanır.  
  
 Türetilen sınıfların bu deseni kullanarak yeni bir algoritma veya varolan bir algoritma için yeni bir uygulama eklemek de kolaydır. Örneğin, yeni bir ortak anahtar algoritması oluşturmak için devralınan <xref:System.Security.Cryptography.AsymmetricAlgorithm> sınıfı. Belirli bir algoritma yeni bir uygulama oluşturmak için bu algoritmasının Özet olmayan türetilmiş bir sınıf oluşturursunuz.  
  
## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>.NET Framework algoritmaları nasıl uygulanır  
 Farklı uygulamaları için bir algoritma kullanılabilir bir örnek olarak, simetrik algoritmaları göz önünde bulundurun. Tüm simetrik algoritmaları temeli <xref:System.Security.Cryptography.SymmetricAlgorithm>, aşağıdaki algoritmaları tarafından devralınan:  
  
1.  <xref:System.Security.Cryptography.Aes>  
  
2.  <xref:System.Security.Cryptography.DES>  
  
3.  <xref:System.Security.Cryptography.RC2>  
  
4.  <xref:System.Security.Cryptography.Rijndael>  
  
5.  <xref:System.Security.Cryptography.TripleDES>  
  
 <xref:System.Security.Cryptography.Aes> iki sınıflar tarafından devralınır: <xref:System.Security.Cryptography.AesCryptoServiceProvider> ve <xref:System.Security.Cryptography.AesManaged>. <xref:System.Security.Cryptography.AesCryptoServiceProvider> Sınıftır Aes, Windows şifreleme API (CAPI) uyarlamasını çevresinde bir sarmalayıcı ancak <xref:System.Security.Cryptography.AesManaged> sınıfı, tamamen yönetilen kodda yazılır. Uygulamasında, yeni nesil şifreleme (CNG), yönetilen eklemeyi ve CAPI uygulamaları üçüncü türü yok. CNG algoritması örneğidir <xref:System.Security.Cryptography.ECDiffieHellmanCng>. CNG algoritmaları ve sonrasında Windows Vista'da kullanılabilir.  
  
 Hangi sizin için en iyi uygulamadır seçebilirsiniz.  Yönetilen uygulamalar, .NET Framework desteği tüm platformlarda kullanılabilir.  CAPI uygulamaları, eski işletim sistemlerinde kullanılabilir ve artık geliştirilmektedir. CNG yeni geliştirme burada gerçekleşecek en son uygulamasıdır. Ancak, yönetilen uygulamaları Federal Bilgi işleme standartları (FIPS tarafından) uygunluğu onaylanmamıştır ve sarmalayıcı sınıflar yavaş olabilir.  
  
## <a name="stream-design"></a>Akış tasarım  
 Ortak dil çalışma zamanı simetrik algoritmaları ve karma algoritmaları uygulamak için bir akış Odaklı Tasarım kullanır. Bu tasarım çekirdeği <xref:System.Security.Cryptography.CryptoStream> türeyen sınıf <xref:System.IO.Stream> sınıfı. Akış tabanlı şifreleme nesnelerini destekleyen tek bir standart arabirimi (`CryptoStream`) nesne veri aktarımı bölümü işlemek için. Tüm nesneler üzerinde standart bir arabirim oluşturulur çünkü birden çok nesne (örneğin, bir şifreleme nesnesi tarafından izlenen bir karma nesnesi) zincir ve herhangi bir ara depolama alanı için gerek kalmadan veriler üzerinde birden çok işlemler gerçekleştirebilirsiniz. Akış modeli daha küçük nesnelerine nesnelerden oluşturmanıza olanak sağlar. Örneğin, bu nesne akışı nesneleri kümesinden yerleştirilmiş olabilir ancak birleşik bir şifreleme ve karma algoritma tek stream nesnesi olarak görüntülenebilir.  
  
## <a name="cryptographic-configuration"></a>Şifreleme yapılandırması  
 Şifreleme yapılandırması, .NET Framework şifreleme sınıflarını genişletilebilirlik sağlayan bir algoritma adı için bir algoritma, belirli bir uygulamasına çözümlemenize olanak tanır. Bir algoritma kendi donanım veya yazılım uygulaması eklemek ve uygulama tercih ettiğiniz algoritma adı eşleyin. Bir algoritma yapılandırma dosyasında belirtilmezse, varsayılan ayarlar kullanılır. Şifreleme yapılandırması hakkında daha fazla bilgi için bkz: [şifreleme sınıflarını yapılandırma](../../../docs/framework/configure-apps/configure-cryptography-classes.md).  
  
## <a name="choosing-an-algorithm"></a>Bir algoritma seçme  
 Çeşitli nedenlerle bir algoritma seçebilirsiniz: Örneğin, veri bütünlüğü, veri gizliliği için ya da bir anahtar oluşturmak için. Simetrik ve karma algoritmaları bütünlüğü nedenleri (değişikliği koruma) veya (görüntülemesini koruma) gizlilik nedeniyle verileri korumak için tasarlanmıştır. Karma algoritmaları öncelikle veri bütünlüğü için kullanılır.  
  
 Uygulama tarafından önerilen algoritmaları listesi aşağıdadır:  
  
-   Veri gizliliği:  
  
    -   <xref:System.Security.Cryptography.Aes>  
  
-   Veri bütünlüğü:  
  
    -   <xref:System.Security.Cryptography.HMACSHA256>  
  
    -   <xref:System.Security.Cryptography.HMACSHA512>  
  
-   Dijital imza:  
  
    -   <xref:System.Security.Cryptography.ECDsa>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   Anahtar Değişimi:  
  
    -   <xref:System.Security.Cryptography.ECDiffieHellman>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   Rastgele sayı oluşturma:  
  
    -   <xref:System.Security.Cryptography.RNGCryptoServiceProvider>  
  
-   Bir anahtar parola durumundan oluşturuluyor:  
  
    -   <xref:System.Security.Cryptography.Rfc2898DeriveBytes>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)  
 
