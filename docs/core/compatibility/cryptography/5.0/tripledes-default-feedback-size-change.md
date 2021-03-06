---
title: 'Son değişiklik: TripleDES tarafından oluşturulan örnekler için varsayılan FeedbackSize değeri. oluşturma değiştirildi'
description: .NET 5 ' teki önemli değişiklik hakkında bilgi edinmek için, TripleDES. Create () tarafından döndürülen TripleDES örneğinde bulunan FeedbackSize özelliğinin varsayılan değeri 64 ' den 8 ' e değişmiştir.
ms.date: 10/16/2020
ms.openlocfilehash: 9d3259da30cce84e83a3f13c610dad5884b445b8
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256770"
---
# <a name="default-feedbacksize-value-for-instances-created-by-tripledescreate-changed"></a>TripleDES tarafından oluşturulan örnekler için varsayılan FeedbackSize değeri. oluşturma değiştirildi

<xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType>Öğesinden döndürülen örnekteki özelliğin varsayılan değeri, <xref:System.Security.Cryptography.TripleDES> <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> .NET Framework geçişinin daha kolay olması için 64 ' den 8 ' e değişmiştir. Doğrudan çağıran kodda kullanılmadığı takdirde bu özellik yalnızca özelliği olduğunda kullanılır <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> .

<xref:System.Security.Cryptography.CipherMode.CFB>Mod desteği ilk olarak 5,0 RC1 sürümü için .net 'e eklenmiştir, bu nedenle yalnızca .NET 5 RC1 ve .NET 5 RC2 uygulamalarının bu değişiklikten etkilenmeleri gerekir.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET Core ve önceki yayın öncesi sürüm sürümlerinde, .NET 5 ' in `TripleDES.Create().FeedbackSize` varsayılan değeri 64 ' dir. .NET 5 ' in RTM sürümünden itibaren `TripleDES.Create().FeedbackSize` varsayılan değer 8 ' i içerir.

## <a name="reason-for-change"></a>Değişiklik nedeni

.NET Framework, <xref:System.Security.Cryptography.TripleDES> temel sınıf değerini 64 olarak belirler <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> , ancak <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> sınıf varsayılan olarak 8 ' e yazar. Özellik, <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> sürüm 2,0 ' de .NET Core 'a sunulsa da aynı davranış korundu. Ancak, .NET Framework ' de <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> bir örneği döndürür <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> , bu nedenle algoritma fabrikasından varsayılan değer 8 ' dir. .NET Core ve .NET 5 + için, algoritma fabrikası genel olmayan bir uygulama döndürür ve bu, şu anda varsayılan 64 değerine sahip olur.

<xref:System.Security.Cryptography.TripleDES>Uygulama sınıfı <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> değerinin 8 olarak değiştirilmesi, şifreleme modunu belirtilen .NET Framework için yazılan uygulamalar için izin verir <xref:System.Security.Cryptography.CipherMode.CFB> <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> , ancak .NET 5 ' te çalışmaya devam etmek için özelliği açıkça atamamıştı.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

.NET 5 ' ün RC1 veya RC2 sürümlerindeki verileri şifreleyen veya şifresini çözen uygulamalar aşağıdaki koşullar karşılandığında CFB64 ile yapılır:

- Bir <xref:System.Security.Cryptography.TripleDES> örneği ile <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> .
- İçin varsayılan değer kullanılıyor <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> .
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode>Özelliği olarak ayarlanır <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> .

Bu davranışı sürdürmek için <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> özelliğini öğesine atayın `64` .

Tüm `TripleDES` uygulamalar için aynı varsayılanı kullanmaz <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> . <xref:System.Security.Cryptography.CipherMode.CFB>Örneklerde şifre modunu kullanırsanız <xref:System.Security.Cryptography.TripleDES> , özellik değerini her zaman açıkça atamanız önerilir <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> .

```csharp
TripleDES cipher = TripleDES.Create();
cipher.Mode = CipherMode.CFB;
// Explicitly set the FeedbackSize for CFB to control between CFB8 and CFB64.
cipher.FeedbackSize = 8;
```

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Security.Cryptography.TripleDES.Create`
- `P:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize`

### Category

- Cryptography

-->
