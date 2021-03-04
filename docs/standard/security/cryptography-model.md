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
# <a name="net-cryptography-model"></a><span data-ttu-id="2394e-104">.NET şifreleme modeli</span><span class="sxs-lookup"><span data-stu-id="2394e-104">.NET cryptography model</span></span>

<span data-ttu-id="2394e-105">.NET birçok standart şifreleme algoritmalarının uygulamalarını sağlar ve .NET şifreleme modeli genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="2394e-105">.NET provides implementations of many standard cryptographic algorithms, and the .NET cryptography model is extensible.</span></span>

## <a name="object-inheritance"></a><span data-ttu-id="2394e-106">Nesne devralma</span><span class="sxs-lookup"><span data-stu-id="2394e-106">Object inheritance</span></span>

<span data-ttu-id="2394e-107">.NET şifreleme sistemi, türetilmiş sınıf devralma için genişletilebilir bir model uygular.</span><span class="sxs-lookup"><span data-stu-id="2394e-107">The .NET cryptography system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="2394e-108">Hiyerarşi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2394e-108">The hierarchy is as follows:</span></span>

- <span data-ttu-id="2394e-109">, Veya gibi algoritma türü sınıfı <xref:System.Security.Cryptography.SymmetricAlgorithm>  <xref:System.Security.Cryptography.AsymmetricAlgorithm> <xref:System.Security.Cryptography.HashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="2394e-109">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm>, or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="2394e-110">Bu düzey soyuttur.</span><span class="sxs-lookup"><span data-stu-id="2394e-110">This level is abstract.</span></span>

- <span data-ttu-id="2394e-111">Algoritma türü sınıfından devralan algoritma sınıfı; Örneğin,, <xref:System.Security.Cryptography.Aes> <xref:System.Security.Cryptography.RSA> veya <xref:System.Security.Cryptography.ECDiffieHellman> .</span><span class="sxs-lookup"><span data-stu-id="2394e-111">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RSA>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="2394e-112">Bu düzey soyuttur.</span><span class="sxs-lookup"><span data-stu-id="2394e-112">This level is abstract.</span></span>

- <span data-ttu-id="2394e-113">Algoritma sınıfından devralan algoritma sınıfının uygulanması; Örneğin,, <xref:System.Security.Cryptography.AesManaged> <xref:System.Security.Cryptography.RC2CryptoServiceProvider> veya <xref:System.Security.Cryptography.ECDiffieHellmanCng> .</span><span class="sxs-lookup"><span data-stu-id="2394e-113">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="2394e-114">Bu düzey tam olarak uygulandı.</span><span class="sxs-lookup"><span data-stu-id="2394e-114">This level is fully implemented.</span></span>

<span data-ttu-id="2394e-115">Bu türetilmiş sınıfların stili, yeni bir algoritma veya var olan algoritmanın yeni bir uygulamasını eklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2394e-115">This pattern of derived classes lets you add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="2394e-116">Örneğin, yeni bir ortak anahtar algoritması oluşturmak için sınıfından devralmasını sağlayabilirsiniz <xref:System.Security.Cryptography.AsymmetricAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="2394e-116">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="2394e-117">Belirli bir algoritmanın yeni bir uygulamasını oluşturmak için, bu algoritmanın soyut olmayan bir türetilmiş sınıfını oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2394e-117">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>

## <a name="how-algorithms-are-implemented-in-net"></a><span data-ttu-id="2394e-118">Algoritmalar .NET 'te nasıl uygulanır</span><span class="sxs-lookup"><span data-stu-id="2394e-118">How algorithms are implemented in .NET</span></span>

<span data-ttu-id="2394e-119">Algoritma için kullanılabilen farklı uygulamalara örnek olarak, simetrik algoritmaları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="2394e-119">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="2394e-120">Tüm simetrik algoritmaların temeli, <xref:System.Security.Cryptography.SymmetricAlgorithm> ve tarafından devralınan, <xref:System.Security.Cryptography.Aes> <xref:System.Security.Cryptography.TripleDES> ve artık önerilmeyen diğerleri.</span><span class="sxs-lookup"><span data-stu-id="2394e-120">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.TripleDES>, and others that are no longer recommended.</span></span>

<span data-ttu-id="2394e-121"><xref:System.Security.Cryptography.Aes><xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.AesCng> , ve tarafından devralınır <xref:System.Security.Cryptography.AesManaged> .</span><span class="sxs-lookup"><span data-stu-id="2394e-121"><xref:System.Security.Cryptography.Aes> is inherited by <xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.AesCng>, and <xref:System.Security.Cryptography.AesManaged>.</span></span>

<span data-ttu-id="2394e-122">Windows üzerinde .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="2394e-122">In .NET Framework on Windows:</span></span>

* <span data-ttu-id="2394e-123">`*CryptoServiceProvider` gibi algoritma sınıfları, <xref:System.Security.Cryptography.AesCryptoServiceProvider> bir algoritmanın Windows şifreleme API 'si (CAPI) uygulamasındaki sarmalayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="2394e-123">`*CryptoServiceProvider` algorithm classes, such as <xref:System.Security.Cryptography.AesCryptoServiceProvider>, are wrappers around the Windows Cryptography API (CAPI) implementation of an algorithm.</span></span>
* <span data-ttu-id="2394e-124">`*Cng` gibi algoritma sınıfları, <xref:System.Security.Cryptography.ECDiffieHellmanCng> Windows şifreleme yeni nesil (CNG) uygulamasının etrafında sarmalayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="2394e-124">`*Cng` algorithm classes, such as <xref:System.Security.Cryptography.ECDiffieHellmanCng>, are wrappers around the Windows Cryptography Next Generation (CNG) implementation.</span></span>
* <span data-ttu-id="2394e-125">`*Managed` gibi sınıflar, <xref:System.Security.Cryptography.AesManaged> tamamen yönetilen kodda yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2394e-125">`*Managed` classes, such as <xref:System.Security.Cryptography.AesManaged>, are written entirely in managed code.</span></span> <span data-ttu-id="2394e-126">`*Managed` uygulamalar Federal bilgi Işleme standartları (FIPS) tarafından sertifikalandırılması ve sarmalayıcı sınıflarından daha yavaş olabilir `*CryptoServiceProvider` `*Cng` .</span><span class="sxs-lookup"><span data-stu-id="2394e-126">`*Managed` implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the `*CryptoServiceProvider` and `*Cng` wrapper classes.</span></span>

<span data-ttu-id="2394e-127">.NET Core ve .NET 5 ve sonraki sürümlerinde, tüm uygulama sınıfları ( `*CryptoServiceProvider` , `*Managed` ve `*Cng` ) IŞLETIM sistemi (OS) algoritmaları için sarmalayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="2394e-127">In .NET Core and .NET 5 and later versions, all implementation classes (`*CryptoServiceProvider`, `*Managed`, and `*Cng`) are wrappers for the operating system (OS) algorithms.</span></span> <span data-ttu-id="2394e-128">İşletim sistemi algoritmaları FIPS sertifikalı ise, .NET FIPS sertifikalı algoritmalar kullanır.</span><span class="sxs-lookup"><span data-stu-id="2394e-128">If the OS algorithms are FIPS-certified, then .NET uses FIPS-certified algorithms.</span></span> <span data-ttu-id="2394e-129">Daha fazla bilgi için bkz. [platformlar arası şifreleme](cross-platform-cryptography.md).</span><span class="sxs-lookup"><span data-stu-id="2394e-129">For more information, see [Cross-Platform Cryptography](cross-platform-cryptography.md).</span></span>

<span data-ttu-id="2394e-130">Çoğu durumda, gibi bir algoritma uygulama sınıfına doğrudan başvurmanız gerekmez `AesCryptoServiceProvider` .</span><span class="sxs-lookup"><span data-stu-id="2394e-130">In most cases, you don't need to directly reference an algorithm implementation class, such as `AesCryptoServiceProvider`.</span></span> <span data-ttu-id="2394e-131">Genellikle ihtiyacınız olan Yöntemler ve Özellikler taban algoritma sınıfında (gibi) `Aes` .</span><span class="sxs-lookup"><span data-stu-id="2394e-131">The methods and properties you typically need are on the base algorithm class, such as `Aes`.</span></span> <span data-ttu-id="2394e-132">Temel algoritma sınıfında bir Factory yöntemi kullanarak varsayılan uygulama sınıfının bir örneğini oluşturun ve temel algoritma sınıfına bakın.</span><span class="sxs-lookup"><span data-stu-id="2394e-132">Create an instance of a default implementation class by using a factory method on the base algorithm class, and refer to the base algorithm class.</span></span> <span data-ttu-id="2394e-133">Örneğin, aşağıdaki örnekte vurgulanan kod satırına bakın:</span><span class="sxs-lookup"><span data-stu-id="2394e-133">For example, see the highlighted line of code in the following example:</span></span>

:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs" highlight="20":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb" highlight="17":::

## <a name="cryptographic-configuration"></a><span data-ttu-id="2394e-134">Şifreleme yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2394e-134">Cryptographic configuration</span></span>

<span data-ttu-id="2394e-135">Şifreleme yapılandırması, bir algoritmanın belirli bir uygulamasını bir algoritma adına çözümlemenizi sağlar ve .NET şifreleme sınıflarının genişletilebilirliğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2394e-135">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET cryptography classes.</span></span> <span data-ttu-id="2394e-136">Bir algoritmanın kendi donanım veya yazılım uygulamanızı ekleyebilir ve uygulamayı tercih ettiğiniz algoritma adına eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2394e-136">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="2394e-137">Yapılandırma dosyasında bir algoritma belirtilmemişse, varsayılan ayarlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2394e-137">If an algorithm is not specified in the configuration file, the default settings are used.</span></span>

## <a name="choose-an-algorithm"></a><span data-ttu-id="2394e-138">Algoritma seçin</span><span class="sxs-lookup"><span data-stu-id="2394e-138">Choose an algorithm</span></span>

<span data-ttu-id="2394e-139">Farklı nedenlerle bir algoritma seçebilirsiniz: Örneğin, veri bütünlüğü için, veri gizliliği veya bir anahtar oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="2394e-139">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="2394e-140">Simetrik ve karma algoritmalar, bütünlük nedenleriyle (değişiklikten koruma) veya gizlilik nedenlerinden (görüntülemeden koruma) verileri korumak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2394e-140">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="2394e-141">Karma algoritmalar öncelikle veri bütünlüğü için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2394e-141">Hash algorithms are used primarily for data integrity.</span></span>

<span data-ttu-id="2394e-142">Uygulamaya göre önerilen algoritmaların bir listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2394e-142">Here is a list of recommended algorithms by application:</span></span>

- <span data-ttu-id="2394e-143">Veri gizliliği:</span><span class="sxs-lookup"><span data-stu-id="2394e-143">Data privacy:</span></span>
  - <xref:System.Security.Cryptography.Aes>
- <span data-ttu-id="2394e-144">Veri bütünlüğü:</span><span class="sxs-lookup"><span data-stu-id="2394e-144">Data integrity:</span></span>
  - <xref:System.Security.Cryptography.HMACSHA256>
  - <xref:System.Security.Cryptography.HMACSHA512>
- <span data-ttu-id="2394e-145">Dijital imza:</span><span class="sxs-lookup"><span data-stu-id="2394e-145">Digital signature:</span></span>
  - <xref:System.Security.Cryptography.ECDsa>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="2394e-146">Anahtar değişimi:</span><span class="sxs-lookup"><span data-stu-id="2394e-146">Key exchange:</span></span>
  - <xref:System.Security.Cryptography.ECDiffieHellman>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="2394e-147">Rastgele sayı oluşturma:</span><span class="sxs-lookup"><span data-stu-id="2394e-147">Random number generation:</span></span>
  - <xref:System.Security.Cryptography.RandomNumberGenerator.Create%2A?displayProperty=nameWithType>
- <span data-ttu-id="2394e-148">Paroladan anahtar oluşturma:</span><span class="sxs-lookup"><span data-stu-id="2394e-148">Generating a key from a password:</span></span>
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a><span data-ttu-id="2394e-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2394e-149">See also</span></span>

- [<span data-ttu-id="2394e-150">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="2394e-150">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="2394e-151">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="2394e-151">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="2394e-152">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="2394e-152">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
