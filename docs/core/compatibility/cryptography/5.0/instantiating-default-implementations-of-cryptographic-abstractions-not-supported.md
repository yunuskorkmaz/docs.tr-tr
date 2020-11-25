---
title: 'Son değişiklik: şifreleme soyut uygulamalarının varsayılan uygulamalarını örnekleme desteklenmiyor'
description: Şifreleme soyutlamaları üzerinde parametresiz Create () aşırı yüklemelerinin artık kullanılmıyor olması durumunda .NET 5,0 'deki önemli değişiklik hakkında bilgi edinin.
ms.date: 10/16/2020
ms.openlocfilehash: 8ed7d0b72347ec41ec65ccd9e4004266619c84f7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761597"
---
# <a name="instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported"></a>Şifrelenmiş soyutlamalar için varsayılan uygulamaların örneği oluşturma desteklenmiyor

`Create()`Şifreleme soyutlamaları üzerinde Parametresiz aşırı yüklemeler, .net 5,0 itibariyle uyarı olarak kullanımdan kalkmıştır.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 2,0-4,8 ' de, gibi soyut şifreleme temel Fabrikası <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> farklı algoritmalar döndürecek şekilde yapılandırılabilir. Örneğin, .NET Framework 4,8 ' nin varsayılan yüklemesinin parametresiz, statik yöntemi, <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> Aşağıdaki kod parçacığında gösterildiği gibi, SHA1 algoritmasının bir örneğini döndürür.

**Yalnızca .NET Framework**

```csharp
// Return an instance of the default hash algorithm (SHA1).
HashAlgorithm alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA1CryptoServiceProvider'.
Console.WriteLine(alg.GetType());

// Change the default algorithm to be SHA256, not SHA1.
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), typeof(HashAlgorithm).FullName);
alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA256CryptoServiceProvider'.
Console.WriteLine(alg.GetType());
```

Ayrıca, programlama yoluyla çağırmak gerekmeden varsayılan algoritmayı değiştirmek için [makine genelinde yapılandırma](../../../../framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) kullanabilirsiniz `CryptoConfig` .

.NET Core 2,0-3,1 ' de, her zaman, gibi soyut şifreleme temel fabrikaları <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> oluşturur <xref:System.PlatformNotSupportedException> .

```csharp
// Throws PlatformNotSupportedException on .NET Core.
HashAlgorithm alg = HashAlgorithm.Create();
```

.NET 5,0 ve sonraki sürümlerinde, gibi soyut şifreleme temel fabrikaları <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> kullanılmıyor olarak işaretlenir ve kimliğiyle derleme zamanı uyarısı üretir `SYSLIB0007` . Çalışma zamanında, bu yöntemler bir oluşturma işlemine devam eder <xref:System.PlatformNotSupportedException> .

```csharp
// Throws PlatformNotSupportedException.
// Also produces compile-time warning SYSLIB0007 on .NET 5+.
HashAlgorithm alg = HashAlgorithm.Create();
```

Bu yalnızca derleme zamanı değişir. .NET Core 'un önceki sürümlerinden çalışma zamanı değişikliği yoktur.

> [!NOTE]
>
> - Yöntemlerin yalnızca Parametresiz aşırı yüklemeleri `Create()` artık kullanılmıyor. Parametreli aşırı yüklemeler artık kullanılmıyor ve beklendiği gibi işlev görmeye devam ediyor.
>
>   ```csharp
>   // Call Create(string), providing an explicit algorithm family name.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   HashAlgorithm hashAlg = HashAlgorithm.Create("SHA256");
>   ```
>
> - *Belirli* algoritma ailelerinin (soyut olmayan) Parametresiz aşırı yüklemeleri artık kullanılmıyor ve beklendiği gibi çalışmaya devam edecek.
>
>   ```csharp
>   // Call a specific algorithm family's parameterless Create() ctor.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   Aes aesAlg = Aes.Create();
>   ```

## <a name="reason-for-change"></a>Değişiklik nedeni

Eski sistem doğru şifreleme çevikliğine izin vermediğinden, .NET Framework 'de bulunan şifreleme yapılandırma sistemi artık .NET Core ve .NET 5.0 + ' da mevcut değildir. .NET 'in geriye dönük uyumluluk gereksinimleri Ayrıca, Framework 'ün şifreleme ile ilgili bazı şifreleme API 'Lerini güncelleştirmesini de yasaklıyor. Örneğin, <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> yöntem .NET Framework 1,0 ' de tanıtılmıştır ve SHA-1 karma algoritması bir grafik durumudur. Yirmi yıl geçti ve artık SHA-1 bozuk kabul edildi, ancak <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> farklı bir algoritma döndürmek için değiştiremedik. Bunun yapılması, uygulama tüketen kabul edilemez bir değişikliği ortaya çıkarabilir.

En iyi yöntem, şifreleme temel öğelerini kullanan kitaplıkların (AES, SHA-* ve RSA gibi) bu temel uygulamaları tüketme konusunda tam denetim altında olması gerektiğini belirler. Gelecekte prova gerektiren uygulamalar, bu temelleri kaydırabilen ve anahtar yönetimi ve şifreleme çevikliği özellikleri ekleyen üst düzey kitaplıkları kullanmalıdır. Bu kitaplıklar genellikle barındırma ortamı tarafından sağlanır. Bir örnek ASP ' dir [. ](/aspnet/core/security/data-protection/)Bu sorunları çağıran uygulama adına IŞLEYEN net 'In veri koruma kitaplığı.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

- Önerilen eylem, çağrıları, örneğin, belirli algoritmalar için fabrika yöntemlerine yapılan çağrılarla birlikte kullanımdan kalkmış API 'Ler olarak değiştirecek <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> . Bu, hangi algoritmaların örneklendiği hakkında tam denetim sağlar.

- Artık Kullanımdan kaldırılmış API 'Leri kullanan .NET Framework uygulamalar tarafından oluşturulan mevcut yüklerle uyumluluğu korumanız gerekiyorsa, aşağıdaki tabloda önerilen değişiklikleri kullanın. Tablo, .NET Framework varsayılan algoritmalardan .NET 5 + eşdeğerlerine bir eşleme sağlar.

  | .NET Framework | .NET Core/.NET 5.0 + uyumlu değiştirme | Açıklamalar |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | SHA-1 algoritması bozuk kabul edilir. Mümkünse daha güçlü bir algoritma kullanmayı düşünün. Daha fazla rehberlik için güvenlik danışmanınıza başvurun. |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | HMACSHA1 algoritması, modern uygulamaların çoğu için önerilmez. Mümkünse daha güçlü bir algoritma kullanmayı düşünün. Daha fazla rehberlik için güvenlik danışmanınıza başvurun. |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | HMACSHA1 algoritması, modern uygulamaların çoğu için önerilmez. Mümkünse daha güçlü bir algoritma kullanmayı düşünün. Daha fazla rehberlik için güvenlik danışmanınıza başvurun. |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

- Eski Parametresiz aşırı yüklemeleri çağırmaya devam etmeniz gerekirse `Create()` , `SYSLIB0007` koddaki uyarıyı gizleyebilirsiniz.

  ```csharp
  #pragma warning disable SYSLIB0007 // Disable the warning.
  HashAlgorithm alg = HashAlgorithm.Create(); // Still throws PNSE.
  #pragma warning restore SYSLIB0007 // Re-enable the warning.
  ```

  Ayrıca, proje dosyanızdaki uyarıyı de gizleyebilirsiniz. Bunun yapılması, projedeki tüm kaynak dosyaları için uyarıyı devre dışı bırakır.

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0007 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0007</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > Gizleme, `SYSLIB0007` burada listelenen şifreleme API 'leri için yalnızca kullanımdan kaldırma uyarılarını devre dışı bırakır. Başka herhangi bir uyarıyı devre dışı bırakır. Ayrıca, uyarıyı bastırsanız bile, kullanımdan kaldırılmakta olan bu API 'Ler hala çalışma zamanında oluşturulur <xref:System.PlatformNotSupportedException> .

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Security.Cryptography.AsymmetricAlgorithm.Create`
- `M:System.Security.Cryptography.HashAlgorithm.Create`
- `M:System.Security.Cryptography.HMAC.Create`
- `M:System.Security.Cryptography.KeyedHashAlgorithm.Create`
- `M:System.Security.Cryptography.SymmetricAlgorithm.Create`

### Category

- Cryptography

-->
