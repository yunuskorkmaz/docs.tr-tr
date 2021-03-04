---
title: .NET şifreleme modeli
description: .NET 'teki olağan şifreleme algoritmalarının uygulamalarını gözden geçirin. Nesne devralmayı, akış tasarımını & yapılandırmayı Genişletilebilir şifreleme modelini öğrenin.
ms.date: 02/26/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], model
- encryption [.NET], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: 2208e36ac4521f43cfd2960d92588c8349a119ca
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106936"
---
# <a name="net-cryptography-model"></a>.NET şifreleme modeli

.NET birçok standart şifreleme algoritmalarının uygulamalarını sağlar ve .NET şifreleme modeli genişletilebilir.

## <a name="object-inheritance"></a>Nesne devralma

.NET şifreleme sistemi, türetilmiş sınıf devralma için genişletilebilir bir model uygular. Hiyerarşi aşağıdaki gibidir:

- , Veya gibi algoritma türü sınıfı <xref:System.Security.Cryptography.SymmetricAlgorithm>  <xref:System.Security.Cryptography.AsymmetricAlgorithm> <xref:System.Security.Cryptography.HashAlgorithm> . Bu düzey soyuttur.

- Algoritma türü sınıfından devralan algoritma sınıfı; Örneğin,, <xref:System.Security.Cryptography.Aes> <xref:System.Security.Cryptography.RSA> veya <xref:System.Security.Cryptography.ECDiffieHellman> . Bu düzey soyuttur.

- Algoritma sınıfından devralan algoritma sınıfının uygulanması; Örneğin,, <xref:System.Security.Cryptography.AesManaged> <xref:System.Security.Cryptography.RC2CryptoServiceProvider> veya <xref:System.Security.Cryptography.ECDiffieHellmanCng> . Bu düzey tam olarak uygulandı.

Bu türetilmiş sınıfların stili, yeni bir algoritma veya var olan algoritmanın yeni bir uygulamasını eklemenize olanak sağlar. Örneğin, yeni bir ortak anahtar algoritması oluşturmak için sınıfından devralmasını sağlayabilirsiniz <xref:System.Security.Cryptography.AsymmetricAlgorithm> . Belirli bir algoritmanın yeni bir uygulamasını oluşturmak için, bu algoritmanın soyut olmayan bir türetilmiş sınıfını oluşturacaksınız.

## <a name="how-algorithms-are-implemented-in-net"></a>Algoritmalar .NET 'te nasıl uygulanır

Algoritma için kullanılabilen farklı uygulamalara örnek olarak, simetrik algoritmaları göz önünde bulundurun. Tüm simetrik algoritmaların temeli, <xref:System.Security.Cryptography.SymmetricAlgorithm> ve tarafından devralınan, <xref:System.Security.Cryptography.Aes> <xref:System.Security.Cryptography.TripleDES> ve artık önerilmeyen diğerleri.

<xref:System.Security.Cryptography.Aes><xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.AesCng> , ve tarafından devralınır <xref:System.Security.Cryptography.AesManaged> .

Windows üzerinde .NET Framework:

* `*CryptoServiceProvider` gibi algoritma sınıfları, <xref:System.Security.Cryptography.AesCryptoServiceProvider> bir algoritmanın Windows şifreleme API 'si (CAPI) uygulamasındaki sarmalayıcılardır.
* `*Cng` gibi algoritma sınıfları, <xref:System.Security.Cryptography.ECDiffieHellmanCng> Windows şifreleme yeni nesil (CNG) uygulamasının etrafında sarmalayıcılardır.
* `*Managed` gibi sınıflar, <xref:System.Security.Cryptography.AesManaged> tamamen yönetilen kodda yazılmıştır. `*Managed` uygulamalar Federal bilgi Işleme standartları (FIPS) tarafından sertifikalandırılması ve sarmalayıcı sınıflarından daha yavaş olabilir `*CryptoServiceProvider` `*Cng` .

.NET Core ve .NET 5 ve sonraki sürümlerinde, tüm uygulama sınıfları ( `*CryptoServiceProvider` , `*Managed` ve `*Cng` ) IŞLETIM sistemi (OS) algoritmaları için sarmalayıcılardır. İşletim sistemi algoritmaları FIPS sertifikalı ise, .NET FIPS sertifikalı algoritmalar kullanır. Daha fazla bilgi için bkz. [platformlar arası şifreleme](cross-platform-cryptography.md).

Çoğu durumda, gibi bir algoritma uygulama sınıfına doğrudan başvurmanız gerekmez `AesCryptoServiceProvider` . Genellikle ihtiyacınız olan Yöntemler ve Özellikler taban algoritma sınıfında (gibi) `Aes` . Temel algoritma sınıfında bir Factory yöntemi kullanarak varsayılan uygulama sınıfının bir örneğini oluşturun ve temel algoritma sınıfına bakın. Örneğin, aşağıdaki örnekte vurgulanan kod satırına bakın:

:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs" highlight="20":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb" highlight="17":::

## <a name="cryptographic-configuration"></a>Şifreleme yapılandırması

Şifreleme yapılandırması, bir algoritmanın belirli bir uygulamasını bir algoritma adına çözümlemenizi sağlar ve .NET şifreleme sınıflarının genişletilebilirliğini sağlar. Bir algoritmanın kendi donanım veya yazılım uygulamanızı ekleyebilir ve uygulamayı tercih ettiğiniz algoritma adına eşleyebilirsiniz. Yapılandırma dosyasında bir algoritma belirtilmemişse, varsayılan ayarlar kullanılır.

## <a name="choose-an-algorithm"></a>Algoritma seçin

Farklı nedenlerle bir algoritma seçebilirsiniz: Örneğin, veri bütünlüğü için, veri gizliliği veya bir anahtar oluşturmak için. Simetrik ve karma algoritmalar, bütünlük nedenleriyle (değişiklikten koruma) veya gizlilik nedenlerinden (görüntülemeden koruma) verileri korumak için tasarlanmıştır. Karma algoritmalar öncelikle veri bütünlüğü için kullanılır.

Uygulamaya göre önerilen algoritmaların bir listesi aşağıda verilmiştir:

- Veri gizliliği:
  - <xref:System.Security.Cryptography.Aes>
- Veri bütünlüğü:
  - <xref:System.Security.Cryptography.HMACSHA256>
  - <xref:System.Security.Cryptography.HMACSHA512>
- Dijital imza:
  - <xref:System.Security.Cryptography.ECDsa>
  - <xref:System.Security.Cryptography.RSA>
- Anahtar değişimi:
  - <xref:System.Security.Cryptography.ECDiffieHellman>
  - <xref:System.Security.Cryptography.RSA>
- Rastgele sayı oluşturma:
  - <xref:System.Security.Cryptography.RandomNumberGenerator.Create%2A?displayProperty=nameWithType>
- Paroladan anahtar oluşturma:
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Hizmetleri](cryptographic-services.md)
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)
