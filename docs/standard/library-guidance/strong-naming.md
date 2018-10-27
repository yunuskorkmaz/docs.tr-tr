---
title: Tanımlayıcı ad oluşturma ve .NET kitaplıkları
description: Tanımlayıcı adlandırma .NET kitaplıkları için en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/16/2018
ms.openlocfilehash: 6f5743c7a8c6fdbdcdcf3aa80d2f92f2e04621f2
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50041774"
---
# <a name="strong-naming"></a><span data-ttu-id="e6576-103">Tanımlayıcı ad oluşturma</span><span class="sxs-lookup"><span data-stu-id="e6576-103">Strong naming</span></span>

<span data-ttu-id="e6576-104">Tanımlayıcı adlandırma başvuruyor üreten bir anahtarla bir derlemeyi imzalamak için bir [tanımlayıcı adlı derleme](../../framework/app-domains/strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="e6576-104">Strong naming refers to signing an assembly with a key, producing a [strong-named assembly](../../framework/app-domains/strong-named-assemblies.md).</span></span> <span data-ttu-id="e6576-105">Kesin adlandırılmış bir derlemedir, adı ve derleme sürüm numarasına göre benzersiz bir kimliği oluşturur ve derleme çakışmalarının önlenmesine yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6576-105">When an assembly is strong-named, it creates a unique identity based on the name and assembly version number, and it can help prevent assembly conflicts.</span></span>

<span data-ttu-id="e6576-106">Tanımlayıcı adlandırma için dezavantajı, bir derleme tanımlayıcı ada sonra Windows üzerinde .NET Framework derlemeleri katı yüklenmesini sağlayan ' dir.</span><span class="sxs-lookup"><span data-stu-id="e6576-106">The downside to strong naming is that the .NET Framework on Windows enables strict loading of assemblies once an assembly is strong named.</span></span> <span data-ttu-id="e6576-107">Bir tanımlayıcı adlı bütünleştirilmiş kod başvurusu geliştiricilerine zorlama, bir derleme tarafından başvurulan sürümü tam olarak eşleşmelidir [bağlama yeniden yönlendirmeleri yapılandırma](../../framework/configure-apps/redirect-assembly-versions.md) derleme kullanırken:</span><span class="sxs-lookup"><span data-stu-id="e6576-107">A strong-named assembly reference must exactly match the version referenced by an assembly, forcing developers to [configure binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) when using the assembly:</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly" publicKeyToken="32ab4ba45e0a69a1" culture="neutral" />
            <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

<span data-ttu-id="e6576-108">.NET geliştiricileri, güçlü adlandırma hakkında şikayet ne bunlar genellikle hakkında şikayetçi katı derleme yükleme olur.</span><span class="sxs-lookup"><span data-stu-id="e6576-108">When .NET developers complain about strong naming, what they're usually complaining about is strict assembly loading.</span></span> <span data-ttu-id="e6576-109">Neyse ki, bu sorun, .NET Framework yalıtılır.</span><span class="sxs-lookup"><span data-stu-id="e6576-109">Fortunately, this issue is isolated to the .NET Framework.</span></span> <span data-ttu-id="e6576-110">.NET core, Xamarin, UWP ve diğer .NET uygulamalarının çoğu katı derleme yükleme yoktur ve tanımlayıcı adlandırmanın temel dezavantajı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e6576-110">.NET Core, Xamarin, UWP, and most other .NET implementations don't have strict assembly loading and removes the main downside of strong naming.</span></span>

<span data-ttu-id="e6576-111">Tanımlayıcı adlandırma önemli yönlerinden biri olan viral: güçlü derleme can yalnızca başvuru diğer güçlü adlı derlemeler adlı.</span><span class="sxs-lookup"><span data-stu-id="e6576-111">One important aspect of strong naming is that it's viral: a strong named assembly can only reference other strong named assemblies.</span></span> <span data-ttu-id="e6576-112">Kitaplığınızı adlı sağlam değilse bir uygulama ya da tanımlayıcı adlandırma kullanmasını gerektiren bir kitaplık oluşturuyorsanız geliştiriciler dışarıda.</span><span class="sxs-lookup"><span data-stu-id="e6576-112">If your library isn't strong named, then you have excluded developers who are building an application or library that needs strong naming from using it.</span></span>

<span data-ttu-id="e6576-113">Tanımlayıcı adlandırma avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e6576-113">The benefits of strong naming are:</span></span>

1. <span data-ttu-id="e6576-114">Derleme, başvurulan ve diğer tanımlayıcı adlı derlemeler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e6576-114">The assembly can be referenced and used by other strong-named assemblies.</span></span>
2. <span data-ttu-id="e6576-115">Derleme Genel Derleme Önbelleği'ne (GAC) depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="e6576-115">The assembly can be stored in the Global Assembly Cache (GAC).</span></span>
3. <span data-ttu-id="e6576-116">Derleme, derlemenin diğer sürümlerle yan yana yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6576-116">The assembly can be loaded side by side with other versions of the assembly.</span></span> <span data-ttu-id="e6576-117">Yan yana derleme yükleme, eklenti mimariler ile uygulamalar tarafından yaygın olarak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e6576-117">Side-by-side assembly loading is commonly required by applications with plug-in architectures.</span></span>

## <a name="create-strong-named-net-libraries"></a><span data-ttu-id="e6576-118">.NET kitaplıkları adlı güçlü oluşturma</span><span class="sxs-lookup"><span data-stu-id="e6576-118">Create strong named .NET libraries</span></span>

<span data-ttu-id="e6576-119">Ayrıca, açık kaynak .NET kitaplıkları strong adlandırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="e6576-119">You should strong name your open-source .NET libraries.</span></span> <span data-ttu-id="e6576-120">Tanımlayıcı ad derleme oluşturma, çoğu kişi kullanın ve .NET Framework katı derleme yalnızca yükleme etkiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6576-120">Strong naming an assembly ensures the most people can use it, and strict assembly loading only affects the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="e6576-121">Nuget.org adresinden .NET kitaplıkları yayımlanan gibi bu genel olarak dağıtılmış .NET kitaplıkları için belirli bir kılavuzdur. Tanımlayıcı adlandırma çoğu .NET uygulamaları tarafından gerekli değildir ve varsayılan olarak gerçekleştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="e6576-121">This guidance is specific to publicly distributed .NET libraries, such as .NET libraries published on NuGet.org. Strong naming is not required by most .NET applications and should not be done by default.</span></span>

<span data-ttu-id="e6576-122">**✔️ DÜŞÜNÜN** güçlü kitaplığınızın derlemelerini adlandırma.</span><span class="sxs-lookup"><span data-stu-id="e6576-122">**✔️ CONSIDER** strong naming your library's assemblies.</span></span>

<span data-ttu-id="e6576-123">**✔️ DÜŞÜNÜN** kaynak denetim sisteminize güçlü adlandırma anahtar ekleme.</span><span class="sxs-lookup"><span data-stu-id="e6576-123">**✔️ CONSIDER** adding the strong naming key to your source control system.</span></span>

> <span data-ttu-id="e6576-124">Genel kullanıma açık bir anahtar geliştiricilerin değiştirmek ve aynı anahtara sahip kitaplık kaynak kodunuzu yeniden derleyin sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6576-124">A publicly available key lets developers modify and recompile your library source code with the same key.</span></span>
> 
> <span data-ttu-id="e6576-125">Güçlü adlandırma anahtar geçmişte, özel izinleri verme kullanıldıysa, genel yap olmamalıdır [kısmi güven senaryoları](/dotnet/framework/misc/using-libraries-from-partially-trusted-code).</span><span class="sxs-lookup"><span data-stu-id="e6576-125">You shouldn't make the strong naming key public if it has been used in the past to give special permissions in [partial-trust scenarios](/dotnet/framework/misc/using-libraries-from-partially-trusted-code).</span></span> <span data-ttu-id="e6576-126">Aksi takdirde, mevcut ortamlar tehlikeye atabilir.</span><span class="sxs-lookup"><span data-stu-id="e6576-126">Otherwise, you might compromise existing environments.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6576-127">Kod bir yayımcının kimliğini istendiğinde [Authenticode](/windows-hardware/drivers/install/authenticode) ve [NuGet paket imzalama](/nuget/create-packages/sign-a-package) önerilir.</span><span class="sxs-lookup"><span data-stu-id="e6576-127">When the identity of the publisher of the code is desired, [Authenticode](/windows-hardware/drivers/install/authenticode) and [NuGet Package Signing](/nuget/create-packages/sign-a-package) are recommended.</span></span> <span data-ttu-id="e6576-128">Kod erişim güvenliği (CAS) bir güvenlik riskini azaltma kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6576-128">Code Access Security (CAS) should not be used as a security mitigation.</span></span>

<span data-ttu-id="e6576-129">**✔️ DÜŞÜNÜN** derleme sürümü yalnızca ana sürüm değişikliklerini bağlama yeniden yönlendirmeleri ve ne sıklıkta güncelleştirilmiş kullanıcılara yardımcı olmak için artırma.</span><span class="sxs-lookup"><span data-stu-id="e6576-129">**✔️ CONSIDER** incrementing the assembly version on only major version changes to help users reduce binding redirects, and how often they're updated.</span></span>

> <span data-ttu-id="e6576-130">Daha fazla bilgi edinin [sürüm oluşturma ve derleme sürümüne](./versioning.md#assembly-version).</span><span class="sxs-lookup"><span data-stu-id="e6576-130">Read more about [versioning and the assembly version](./versioning.md#assembly-version).</span></span>

<span data-ttu-id="e6576-131">**❌ SAĞLAMADIĞI** eklemek, kaldırmak veya tanımlayıcı adlandırma anahtarını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e6576-131">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

> <span data-ttu-id="e6576-132">Bir derlemenin tanımlayıcı adlandırma anahtarını değiştirerek, derlemenin kimliğini değiştirir ve kullandığı derlenmiş kodları keser.</span><span class="sxs-lookup"><span data-stu-id="e6576-132">Modifying an assembly's strong naming key changes the assembly's identity and breaks compiled code that uses it.</span></span> <span data-ttu-id="e6576-133">Daha fazla bilgi için [ikili bozucu değişiklikler](./breaking-changes.md#binary-breaking-change).</span><span class="sxs-lookup"><span data-stu-id="e6576-133">For more information, see [binary breaking changes](./breaking-changes.md#binary-breaking-change).</span></span>

<span data-ttu-id="e6576-134">**❌ SAĞLAMADIĞI** kitaplığınızın tanımlayıcı adlı ve olmayan-tanımlayıcı adlı sürümler yayımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e6576-134">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="e6576-135">Örneğin, `Contoso.Api` ve `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="e6576-135">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

> <span data-ttu-id="e6576-136">İki paketleri çatalları Geliştirici ekonomik sistem yayımlanıyor.</span><span class="sxs-lookup"><span data-stu-id="e6576-136">Publishing two packages forks your developer eco-system.</span></span> <span data-ttu-id="e6576-137">Ayrıca, uygulamaya bağlı olarak iki paketi de sona erecek, geliştirici türü adı çakışmaları olarak sınırlamasıyla.</span><span class="sxs-lookup"><span data-stu-id="e6576-137">Also, if an application ends up depending on both packages the developer can encounter type name conflicts.</span></span> <span data-ttu-id="e6576-138">.NET ilgili olduğu kadar farklı derlemelerde farklı türlerini değildirler.</span><span class="sxs-lookup"><span data-stu-id="e6576-138">As far as .NET is concerned they are different types in different assemblies.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="e6576-139">[Önceki](./cross-platform-targeting.md)
[İleri](./nuget.md)</span><span class="sxs-lookup"><span data-stu-id="e6576-139">[Previous](./cross-platform-targeting.md)
[Next](./nuget.md)</span></span>
