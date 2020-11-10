---
title: SYSLIB0007 uyarısı
description: Derleme zamanı uyarı SYSLIB0007 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 4c0feac1d673e3462a4f2db470825b15cf1b1706
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439948"
---
# <a name="syslib0007-default-implementations-of-cryptography-algorithms-not-supported"></a>SYSLIB0007: şifreleme algoritmalarının varsayılan uygulamaları desteklenmez

.NET Framework ' deki şifreleme yapılandırma sistemi, uygun şifreleme çevikliğine izin vermez ve .NET Core ve .NET 5 + ' da mevcut değildir. . NET ' in geri uyumluluk gereksinimleri Ayrıca, Framework 'ün şifreleme ile ilgili bazı şifreleme API 'Lerini güncelleştirmesini sağlar. Sonuç olarak, aşağıdaki API 'Ler .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir. Bu API 'lerin kullanımı, `SYSLIB0007` derleme zamanında uyarı oluşturur.

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

## <a name="workarounds"></a>Geçici Çözümler

- Önerilen eylem, çağrıları, örneğin, belirli algoritmalar için fabrika yöntemlerine yapılan çağrılarla birlikte kullanımdan kalkmış API 'Ler olarak değiştirecek <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> . Bu, hangi algoritmaların örneklendiği hakkında tam denetim sağlar.

- Artık Kullanımdan kaldırılmış API 'Leri kullanan .NET Framework uygulamalar tarafından oluşturulan mevcut yüklerle uyumluluğu korumanız gerekiyorsa, aşağıdaki tabloda önerilen değişiklikleri kullanın. Tablo, .NET Framework varsayılan algoritmalardan .NET 5 + eşdeğerlerine bir eşleme sağlar.

  | .NET Framework | .NET Core/.NET 5.0 + uyumlu değiştirme | Açıklamalar |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | SHA-1 algoritması bozuk kabul edilir. Mümkünse daha güçlü bir algoritma kullanmayı düşünün. Daha fazla rehberlik için güvenlik danışmanınıza başvurun. |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | HMACSHA1 algoritması, modern uygulamaların çoğu için önerilmez. Mümkünse daha güçlü bir algoritma kullanmayı düşünün. Daha fazla rehberlik için güvenlik danışmanınıza başvurun. |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | HMACSHA1 algoritması, modern uygulamaların çoğu için önerilmez. Mümkünse daha güçlü bir algoritma kullanmayı düşünün. Daha fazla rehberlik için güvenlik danışmanınıza başvurun. |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme son değişiklikleri](cryptography.md#instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported)
