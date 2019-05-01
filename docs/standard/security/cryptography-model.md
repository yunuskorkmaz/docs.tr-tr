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
ms.openlocfilehash: 7a60f03d85997d20b54366360f104519c9c75f5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795271"
---
# <a name="net-framework-cryptography-model"></a>.NET Framework Şifreleme Modeli

.NET Framework, pek çok standart şifreleme algoritmasını uygulamalarını sağlar. Bu algoritmalar güvenli olası varsayılan özelliklerini kullanıyorsanız ve kolaydır. Ayrıca, .NET Framework şifreleme modeli nesne devralma, akış tasarım ve yapılandırma son derece genişletilebilir.

## <a name="object-inheritance"></a>Nesne Devralma

.NET Framework güvenlik sistemini genişletilebilir bir türetilmiş sınıf devralma deseni uygular. Hiyerarşi aşağıdaki gibidir:

- Algoritma türü sınıfı, gibi <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> veya <xref:System.Security.Cryptography.HashAlgorithm>. Bu düzey soyuttur.

- Algoritma sınıfı bir algoritma türü sınıfından devralır; Örneğin, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, veya <xref:System.Security.Cryptography.ECDiffieHellman>. Bu düzey soyuttur.

- Bir algoritma sınıfından devralan bir algoritma sınıfı uygulaması; Örneğin, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, veya <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Bu düzey, tam olarak uygulanabilir.

Türetilen sınıfların bu düzeni kullanarak, yeni bir algoritma veya mevcut bir algoritmanın yeni bir uygulama eklemek kolaydır. Örneğin, yeni bir ortak anahtar algoritması oluşturmak için öğesinden devralır <xref:System.Security.Cryptography.AsymmetricAlgorithm> sınıfı. Belirli bir algoritma yeni bir uygulama oluşturmak için bu algoritmayı, soyut olmayan türetilmiş bir sınıf oluşturursunuz.

## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>.NET Framework'teki algoritmaları nasıl uygulanır

Farklı uygulamaları bir algoritma için kullanılabilir bir örnek olarak, simetrik algoritmaları göz önünde bulundurun. Temeli tüm simetrik algoritmaları için <xref:System.Security.Cryptography.SymmetricAlgorithm>, aşağıdaki algoritmaları tarafından devralınan:

1. <xref:System.Security.Cryptography.Aes>

2. <xref:System.Security.Cryptography.DES>

3. <xref:System.Security.Cryptography.RC2>

4. <xref:System.Security.Cryptography.Rijndael>

5. <xref:System.Security.Cryptography.TripleDES>

<xref:System.Security.Cryptography.Aes> iki sınıfları tarafından devralındığından: <xref:System.Security.Cryptography.AesCryptoServiceProvider> ve <xref:System.Security.Cryptography.AesManaged>. <xref:System.Security.Cryptography.AesCryptoServiceProvider> Sınıfı, Aes, Windows şifreleme API'si (CAPI) uygulamasının çevresinde sarmalayıcı ise <xref:System.Security.Cryptography.AesManaged> sınıfı, tamamen yönetilen kodda yazılır. Uygulama, şifreleme yeni nesil (CNG), yönetilen eklemeyi ve CAPI uygulamalarında üçüncü bir tür yoktur. CNG algoritması örneğidir <xref:System.Security.Cryptography.ECDiffieHellmanCng>. CNG algoritmaları kullanılabilir Windows Vista ve üstü.

Hangi uygulamayı sizin için en iyi seçebilirsiniz.  Yönetilen uygulamaları, .NET Framework'ü destekleyen tüm platformlarda kullanılamaz.  CAPI uygulamaları daha eski işletim sistemlerinde kullanılabilir olan ve artık geliştirilmektedir. CNG yeni geliştirme projeleri burada gerçekleşecek en son uygulamasıdır. Ancak, yönetilen uygulamalar, Federal Bilgi işleme standartları (FIPS tarafından) onaylanmamıştır ve sarmalayıcı sınıfları yavaş olabilir.

## <a name="stream-design"></a>Stream tasarım

Ortak dil çalışma zamanı, simetrik algoritmalar ve karma algoritmaları uygulamak için bir akış Odaklı Tasarım kullanır. Bu tasarım temel <xref:System.Security.Cryptography.CryptoStream> türetilen sınıf <xref:System.IO.Stream> sınıfı. Stream tabanlı şifreleme nesneler tek ve standart bir arabirimi destekler (`CryptoStream`) nesnesi veri aktarımı bölümünü işlemek için. Tüm nesneleri standart bir arabirimdeki yerleşik olduğundan, birden çok nesne (örneğin, bir şifreleme nesne tarafından izlenen bir karma nesnesi) araya zincirleyebilirsiniz ve herhangi bir ara depolama için gerek kalmadan birden çok veri işlemleri gerçekleştirebilirsiniz. Akış modelinde, daha küçük nesneleri nesneleri oluşturmanızı sağlar. Örneğin, bu nesne, akışı nesneleri kümesinden oluşturulmuş ancak birleşik bir şifreleme ve karma algoritması bir tek akış nesnesi olarak görüntülenebilir.

## <a name="cryptographic-configuration"></a>Şifreleme yapılandırması

Şifreleme yapılandırması bir algoritmanın belirli bir uygulama, .NET Framework şifreleme sınıflarını genişletilebilirlik sağlayan bir algoritma adının çözümlemenize olanak tanır. Kendi donanım veya yazılım uygulaması bir algoritma ekleyebilir ve uygulama ettiğiniz algoritması adı eşleme. Bir algoritma yapılandırma dosyasında belirtilmemişse, varsayılan ayarlar kullanılır. Şifreleme yapılandırması hakkında daha fazla bilgi için bkz: [şifreleme sınıflarını yapılandırma](../../../docs/framework/configure-apps/configure-cryptography-classes.md).

## <a name="choosing-an-algorithm"></a>Algoritma seçme

Farklı nedenlerden dolayı bir algoritma seçebilirsiniz: Örneğin, veri bütünlüğü, veri gizliliği için veya bir anahtar oluşturmak için. Simetrik ve karma algoritmaları bütünlüğünü korumak (değişiklik koruma) ya da gizlilik nedenleriyle (görüntülemesini koruma) verileri korumak için tasarlanmıştır. Karma algoritmaları, öncelikli olarak veri bütünlüğü için kullanılır.

Uygulama tarafından önerilen algoritmaları listesi aşağıda verilmiştir:

- Veri gizliliği:

  - <xref:System.Security.Cryptography.Aes>

- Veri bütünlüğü:

  - <xref:System.Security.Cryptography.HMACSHA256>

  - <xref:System.Security.Cryptography.HMACSHA512>

- Dijital imza:

  - <xref:System.Security.Cryptography.ECDsa>

  - <xref:System.Security.Cryptography.RSA>

- Anahtar değişim:

  - <xref:System.Security.Cryptography.ECDiffieHellman>

  - <xref:System.Security.Cryptography.RSA>

- Rastgele sayı oluşturma:

  - <xref:System.Security.Cryptography.RNGCryptoServiceProvider>

- Bir anahtarı bir paroladan oluşturma:

  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
