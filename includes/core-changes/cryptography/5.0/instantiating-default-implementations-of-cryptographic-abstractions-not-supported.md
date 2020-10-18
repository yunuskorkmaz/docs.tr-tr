---
ms.openlocfilehash: 8198eca5b9c63d9717260b71ac6687dbf7245f35
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159566"
---
### <a name="instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported"></a><span data-ttu-id="81f25-101">Şifrelenmiş soyutlamalar için varsayılan uygulamaların örneği oluşturma desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="81f25-101">Instantiating default implementations of cryptographic abstractions is not supported</span></span>

<span data-ttu-id="81f25-102">`Create()`Şifreleme soyutlamaları üzerinde Parametresiz aşırı yüklemeler, .net 5,0 itibariyle uyarı olarak kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="81f25-102">The parameterless `Create()` overloads on cryptographic abstractions are obsolete as warning as of .NET 5.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="81f25-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="81f25-103">Change description</span></span>

<span data-ttu-id="81f25-104">.NET Framework 2,0-4,8 ' de, gibi soyut şifreleme temel Fabrikası <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> farklı algoritmalar döndürecek şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="81f25-104">In .NET Framework 2.0 - 4.8, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> can be configured to return different algorithms.</span></span> <span data-ttu-id="81f25-105">Örneğin, .NET Framework 4,8 ' nin varsayılan yüklemesinin parametresiz, statik yöntemi, <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> Aşağıdaki kod parçacığında gösterildiği gibi, SHA1 algoritmasının bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="81f25-105">For example, on a default install of .NET Framework 4.8, the parameterless, static method <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> returns an instance of the SHA1 algorithm, as shown in the following snippet.</span></span>

<span data-ttu-id="81f25-106">**Yalnızca .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="81f25-106">**.NET Framework only**</span></span>

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

<span data-ttu-id="81f25-107">Ayrıca, programlama yoluyla çağırmak gerekmeden varsayılan algoritmayı değiştirmek için [makine genelinde yapılandırma](../../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) kullanabilirsiniz `CryptoConfig` .</span><span class="sxs-lookup"><span data-stu-id="81f25-107">You can also use [machine-wide configuration](../../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) to change the default algorithm without needing to call into `CryptoConfig` programmatically.</span></span>

<span data-ttu-id="81f25-108">.NET Core 2,0-3,1 ' de, her zaman, gibi soyut şifreleme temel fabrikaları <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> oluşturur <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="81f25-108">In .NET Core 2.0 - 3.1, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> always throw a <xref:System.PlatformNotSupportedException>.</span></span>

```csharp
// Throws PlatformNotSupportedException on .NET Core.
HashAlgorithm alg = HashAlgorithm.Create();
```

<span data-ttu-id="81f25-109">.NET 5,0 ve sonraki sürümlerinde, gibi soyut şifreleme temel fabrikaları <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> kullanılmıyor olarak işaretlenir ve kimliğiyle derleme zamanı uyarısı üretir `SYSLIB0007` .</span><span class="sxs-lookup"><span data-stu-id="81f25-109">In .NET 5.0 and later versions, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> are marked obsolete and produce a compile-time warning with ID `SYSLIB0007`.</span></span> <span data-ttu-id="81f25-110">Çalışma zamanında, bu yöntemler bir oluşturma işlemine devam eder <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="81f25-110">At run time, these methods continue to throw a <xref:System.PlatformNotSupportedException>.</span></span>

```csharp
// Throws PlatformNotSupportedException.
// Also produces compile-time warning SYSLIB0007 on .NET 5+.
HashAlgorithm alg = HashAlgorithm.Create();
```

<span data-ttu-id="81f25-111">Bu yalnızca derleme zamanı değişir.</span><span class="sxs-lookup"><span data-stu-id="81f25-111">This is a compile-time only change.</span></span> <span data-ttu-id="81f25-112">.NET Core 'un önceki sürümlerinden çalışma zamanı değişikliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="81f25-112">There is no run-time change from previous versions of .NET Core.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="81f25-113">Yöntemlerin yalnızca Parametresiz aşırı yüklemeleri `Create()` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="81f25-113">Only the parameterless overloads of the `Create()` methods are obsolete.</span></span> <span data-ttu-id="81f25-114">Parametreli aşırı yüklemeler artık kullanılmıyor ve beklendiği gibi işlev görmeye devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="81f25-114">Parameterized overloads are not obsolete and still function as expected.</span></span>
>
>   ```csharp
>   // Call Create(string), providing an explicit algorithm family name.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   HashAlgorithm hashAlg = HashAlgorithm.Create("SHA256");
>   ```
>
> - <span data-ttu-id="81f25-115">*Belirli* algoritma ailelerinin (soyut olmayan) Parametresiz aşırı yüklemeleri artık kullanılmıyor ve beklendiği gibi çalışmaya devam edecek.</span><span class="sxs-lookup"><span data-stu-id="81f25-115">Parameterless overloads of *specific* algorithm families (not abstractions) are not obsolete, and will continue to function as expected.</span></span>
>
>   ```csharp
>   // Call a specific algorithm family's parameterless Create() ctor.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   Aes aesAlg = Aes.Create();
>   ```

#### <a name="reason-for-change"></a><span data-ttu-id="81f25-116">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="81f25-116">Reason for change</span></span>

<span data-ttu-id="81f25-117">Eski sistem doğru şifreleme çevikliğine izin vermediğinden, .NET Framework 'de bulunan şifreleme yapılandırma sistemi artık .NET Core ve .NET 5.0 + ' da mevcut değildir.</span><span class="sxs-lookup"><span data-stu-id="81f25-117">The cryptographic configuration system present in .NET Framework is no longer present in .NET Core and .NET 5.0+, since that legacy system doesn't allow for proper cryptographic agility.</span></span> <span data-ttu-id="81f25-118">. NET ' in geri uyumluluk gereksinimleri Ayrıca, Framework 'ün şifreleme ile ilgili bazı şifreleme API 'Lerini güncelleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="81f25-118">.NET's backward-compatibility requirements also prohibit the framework from updating certain cryptographic APIs to keep up with advances in cryptography.</span></span> <span data-ttu-id="81f25-119">Örneğin, <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> yöntem .NET Framework 1,0 ' de tanıtılmıştır ve SHA-1 karma algoritması bir grafik durumudur.</span><span class="sxs-lookup"><span data-stu-id="81f25-119">For example, the <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> method was introduced in .NET Framework 1.0, when the SHA-1 hash algorithm was state-of-the-art.</span></span> <span data-ttu-id="81f25-120">Yirmi yıl geçti ve artık SHA-1 bozuk kabul edildi, ancak <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> farklı bir algoritma döndürmek için değiştiremedik.</span><span class="sxs-lookup"><span data-stu-id="81f25-120">Twenty years have passed, and now SHA-1 is considered broken, but we cannot change <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> to return a different algorithm.</span></span> <span data-ttu-id="81f25-121">Bunun yapılması, uygulama tüketen kabul edilemez bir değişikliği ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="81f25-121">Doing so would introduce an unacceptable breaking change in consuming applications.</span></span>

<span data-ttu-id="81f25-122">En iyi yöntem, şifreleme temel öğelerini kullanan kitaplıkların (AES, SHA-\* ve RSA gibi) bu temel uygulamaları tüketme konusunda tam denetim altında olması gerektiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="81f25-122">Best practice dictates that libraries that consume cryptographic primitives (such as AES, SHA-\*, and RSA) should be in full control over how they consume these primitives.</span></span> <span data-ttu-id="81f25-123">Gelecekte prova gerektiren uygulamalar, bu temelleri kaydırabilen ve anahtar yönetimi ve şifreleme çevikliği özellikleri ekleyen üst düzey kitaplıkları kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="81f25-123">Applications that require future-proofing should utilize higher-level libraries that wrap these primitives and add key management and cryptographic agility capabilities.</span></span> <span data-ttu-id="81f25-124">Bu kitaplıklar genellikle barındırma ortamı tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="81f25-124">These libraries are often provided by the hosting environment.</span></span> <span data-ttu-id="81f25-125">Bir örnek ASP ' dir [. ](/aspnet/core/security/data-protection/)Bu sorunları çağıran uygulama adına IŞLEYEN net 'In veri koruma kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="81f25-125">One example is [ASP.NET's Data Protection library](/aspnet/core/security/data-protection/), which handles these concerns on behalf of the calling application.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="81f25-126">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="81f25-126">Version introduced</span></span>

<span data-ttu-id="81f25-127">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="81f25-127">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="81f25-128">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="81f25-128">Recommended action</span></span>

- <span data-ttu-id="81f25-129">Önerilen eylem, çağrıları, örneğin, belirli algoritmalar için fabrika yöntemlerine yapılan çağrılarla birlikte kullanımdan kalkmış API 'Ler olarak değiştirecek <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="81f25-129">The recommended course of action is to replace calls to the now-obsolete APIs with calls to factory methods for specific algorithms, for example, <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType>.</span></span> <span data-ttu-id="81f25-130">Bu, hangi algoritmaların örneklendiği hakkında tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="81f25-130">This gives you full control over which algorithms are instantiated.</span></span>

- <span data-ttu-id="81f25-131">Artık Kullanımdan kaldırılmış API 'Leri kullanan .NET Framework uygulamalar tarafından oluşturulan mevcut yüklerle uyumluluğu korumanız gerekiyorsa, aşağıdaki tabloda önerilen değişiklikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="81f25-131">If you need to maintain compatibility with existing payloads generated by .NET Framework apps that use the now-obsolete APIs, use the replacements suggested in the following table.</span></span> <span data-ttu-id="81f25-132">Tablo, .NET Framework varsayılan algoritmalardan .NET 5 + eşdeğerlerine bir eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="81f25-132">The table provides a mapping from .NET Framework default algorithms to their .NET 5+ equivalents.</span></span>

  | <span data-ttu-id="81f25-133">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="81f25-133">.NET Framework</span></span> | <span data-ttu-id="81f25-134">.NET Core/.NET 5.0 + uyumlu değiştirme</span><span class="sxs-lookup"><span data-stu-id="81f25-134">.NET Core / .NET 5.0+ compatible replacement</span></span> | <span data-ttu-id="81f25-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81f25-135">Remarks</span></span> |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | <span data-ttu-id="81f25-136">SHA-1 algoritması bozuk kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="81f25-136">The SHA-1 algorithm is considered broken.</span></span> <span data-ttu-id="81f25-137">Mümkünse daha güçlü bir algoritma kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="81f25-137">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="81f25-138">Daha fazla rehberlik için güvenlik danışmanınıza başvurun.</span><span class="sxs-lookup"><span data-stu-id="81f25-138">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="81f25-139">HMACSHA1 algoritması, modern uygulamaların çoğu için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="81f25-139">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="81f25-140">Mümkünse daha güçlü bir algoritma kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="81f25-140">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="81f25-141">Daha fazla rehberlik için güvenlik danışmanınıza başvurun.</span><span class="sxs-lookup"><span data-stu-id="81f25-141">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="81f25-142">HMACSHA1 algoritması, modern uygulamaların çoğu için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="81f25-142">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="81f25-143">Mümkünse daha güçlü bir algoritma kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="81f25-143">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="81f25-144">Daha fazla rehberlik için güvenlik danışmanınıza başvurun.</span><span class="sxs-lookup"><span data-stu-id="81f25-144">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

- <span data-ttu-id="81f25-145">Eski Parametresiz aşırı yüklemeleri çağırmaya devam etmeniz gerekirse `Create()` , `SYSLIB0007` koddaki uyarıyı gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81f25-145">If you must continue to call the obsolete parameterless `Create()` overloads, you can suppress the `SYSLIB0007` warning in code.</span></span>

  ```csharp
  #pragma warning disable SYSLIB0007 // Disable the warning.
  HashAlgorithm alg = HashAlgorithm.Create(); // Still throws PNSE.
  #pragma warning restore SYSLIB0007 // Re-enable the warning.
  ```

  <span data-ttu-id="81f25-146">Ayrıca, proje dosyanızdaki uyarıyı de gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81f25-146">You can also suppress the warning in your project file.</span></span> <span data-ttu-id="81f25-147">Bunun yapılması, projedeki tüm kaynak dosyaları için uyarıyı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="81f25-147">Doing so disables the warning for all source files within the project.</span></span>

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
  > <span data-ttu-id="81f25-148">Gizleme, `SYSLIB0007` burada listelenen şifreleme API 'leri için yalnızca kullanımdan kaldırma uyarılarını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="81f25-148">Suppressing `SYSLIB0007` disables only the obsoletion warnings for the cryptography APIs listed here.</span></span> <span data-ttu-id="81f25-149">Başka herhangi bir uyarıyı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="81f25-149">It does not disable any other warnings.</span></span> <span data-ttu-id="81f25-150">Ayrıca, uyarıyı bastırsanız bile, kullanımdan kaldırılmakta olan bu API 'Ler hala çalışma zamanında oluşturulur <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="81f25-150">Additionally, even if you suppress the warning, these obsoleted APIs will still throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

#### <a name="category"></a><span data-ttu-id="81f25-151">Kategori</span><span class="sxs-lookup"><span data-stu-id="81f25-151">Category</span></span>

- <span data-ttu-id="81f25-152">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="81f25-152">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="81f25-153">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="81f25-153">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.AsymmetricAlgorithm.Create`
- `M:System.Security.Cryptography.HashAlgorithm.Create`
- `M:System.Security.Cryptography.HMAC.Create`
- `M:System.Security.Cryptography.KeyedHashAlgorithm.Create`
- `M:System.Security.Cryptography.SymmetricAlgorithm.Create`

-->
