---
title: .NET Framework Şifreleme Modeli
description: .NET 'teki olağan şifreleme algoritmalarının uygulamalarını gözden geçirin. Nesne devralmayı, akış tasarımını & yapılandırmayı Genişletilebilir şifreleme modelini öğrenin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: 11af4c15c8b291df898a3c2416faa15875eab70b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596325"
---
# <a name="net-framework-cryptography-model"></a>.NET Framework Şifreleme Modeli

.NET Framework birçok standart şifreleme algoritmalarının uygulamalarını sağlar. Bu algoritmaların kullanımı kolaydır ve mümkün olan en güvenli varsayılan özelliklere sahiptir. Ayrıca, nesne devralım, akış tasarımı ve yapılandırmanın .NET Framework şifreleme modeli son derece genişletilebilir.

## <a name="object-inheritance"></a>Nesne devralma

.NET Framework güvenlik sistemi, türetilmiş sınıf devralma için genişletilebilir bir model uygular. Hiyerarşi aşağıdaki gibidir:

- Veya gibi algoritma türü sınıfı <xref:System.Security.Cryptography.SymmetricAlgorithm> <xref:System.Security.Cryptography.AsymmetricAlgorithm> <xref:System.Security.Cryptography.HashAlgorithm> . Bu düzey soyuttur.

- Algoritma türü sınıfından devralan algoritma sınıfı; Örneğin,, <xref:System.Security.Cryptography.Aes> <xref:System.Security.Cryptography.RC2> veya <xref:System.Security.Cryptography.ECDiffieHellman> . Bu düzey soyuttur.

- Algoritma sınıfından devralan algoritma sınıfının uygulanması; Örneğin,, <xref:System.Security.Cryptography.AesManaged> <xref:System.Security.Cryptography.RC2CryptoServiceProvider> veya <xref:System.Security.Cryptography.ECDiffieHellmanCng> . Bu düzey tam olarak uygulandı.

Bu türetilmiş sınıfların modelini kullanarak, yeni bir algoritma veya var olan algoritmanın yeni bir uygulamasını eklemek kolaydır. Örneğin, yeni bir ortak anahtar algoritması oluşturmak için sınıfından devralmasını sağlayabilirsiniz <xref:System.Security.Cryptography.AsymmetricAlgorithm> . Belirli bir algoritmanın yeni bir uygulamasını oluşturmak için, bu algoritmanın soyut olmayan bir türetilmiş sınıfını oluşturacaksınız.

## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>Algoritmaların .NET Framework nasıl uygulandığı

Algoritma için kullanılabilen farklı uygulamalara örnek olarak, simetrik algoritmaları göz önünde bulundurun. Tüm simetrik algoritmaların temeli <xref:System.Security.Cryptography.SymmetricAlgorithm> aşağıdaki algoritmaların Devralındığı anlamına gelir:

* <xref:System.Security.Cryptography.Aes>
* <xref:System.Security.Cryptography.DES>
* <xref:System.Security.Cryptography.RC2>
* <xref:System.Security.Cryptography.Rijndael>
* <xref:System.Security.Cryptography.TripleDES>

<xref:System.Security.Cryptography.Aes>iki sınıf tarafından devralınır: <xref:System.Security.Cryptography.AesCryptoServiceProvider> ve <xref:System.Security.Cryptography.AesManaged> . <xref:System.Security.Cryptography.AesCryptoServiceProvider>Sınıfı, AES 'Nin Windows şifreleme API 'si (CAPI) uygulamasındaki bir sarmalayıcıdır, ancak <xref:System.Security.Cryptography.AesManaged> sınıf tamamen yönetilen kodda yazılır. Ayrıca, yönetilen ve CAPı uygulamalarına ek olarak, bir sonraki nesil şifreleme (CNG) gibi üçüncü bir uygulama türü de vardır. CNG algoritmasına bir örnek vardır <xref:System.Security.Cryptography.ECDiffieHellmanCng> . CNG algoritmaları Windows Vista ve sonraki sürümlerde kullanılabilir.

Hangi uygulamanın sizin için en uygun olduğunu seçebilirsiniz. Yönetilen uygulamalar .NET Framework destekleyen tüm platformlarda kullanılabilir. CAPı uygulamaları daha eski işletim sistemlerinde kullanılabilir ve artık geliştirilmiyor. CNG, yeni geliştirmenin gerçekleşmesi için en son uygulamasıdır. Ancak, yönetilen uygulamalar Federal bilgi Işleme standartları (FIPS) tarafından sertifikalandırılması ve sarmalayıcı sınıflarından daha yavaş olabilir.

## <a name="stream-design"></a>Akış tasarımı

Ortak dil çalışma zamanı, simetrik algoritmaları ve karma algoritmaları uygulamak için akış yönelimli bir tasarım kullanır. Bu tasarımın çekirdeği <xref:System.Security.Cryptography.CryptoStream> sınıfından türetilen sınıftır <xref:System.IO.Stream> . Akış tabanlı şifreleme nesneleri `CryptoStream` , nesnenin veri aktarımı bölümünü işlemek için tek bir standart arabirimi () destekler. Tüm nesneler standart bir arabirim üzerinde oluşturulduğundan, birden fazla nesneyi (bir karma nesnesi ve ardından bir şifreleme nesnesi) birlikte zincirleyebilir ve veri üzerinde herhangi bir ara depolamaya gerek duymadan birden çok işlem gerçekleştirebilirsiniz. Akış modeli, daha küçük nesnelerden nesneler oluşturmanıza de olanak sağlar. Örneğin, bir birleştirilmiş şifreleme ve karma algoritması tek bir Stream nesnesi olarak görüntülenebilir, ancak bu nesne bir akış nesneleri kümesinden oluşturulmuş olabilir.

## <a name="cryptographic-configuration"></a>Şifreleme yapılandırması

Şifreleme yapılandırması, bir algoritmanın belirli bir uygulamasını bir algoritma adına çözümlemenizi sağlar ve .NET Framework şifreleme sınıflarının genişletilebilirliğini sağlar. Bir algoritmanın kendi donanım veya yazılım uygulamanızı ekleyebilir ve uygulamayı tercih ettiğiniz algoritma adına eşleyebilirsiniz. Yapılandırma dosyasında bir algoritma belirtilmemişse, varsayılan ayarlar kullanılır. Şifreleme yapılandırması hakkında daha fazla bilgi için bkz. [şifreleme sınıflarını yapılandırma](../../framework/configure-apps/configure-cryptography-classes.md).

## <a name="choosing-an-algorithm"></a>Algoritma seçme

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
  - <xref:System.Security.Cryptography.RNGCryptoServiceProvider>
- Paroladan anahtar oluşturma:
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Hizmetleri](cryptographic-services.md)
- [C 'de, deneme CE Schneier göre uygulanan şifreleme protokolleri, algoritmalar ve kaynak kodu](https://www.schneier.com/books/applied_cryptography/)
