---
title: Güçlü adlandırma ve .NET kitaplıkları
description: Güçlü adlandırma .NET kitaplıkları için en iyi yöntem önerileri.
ms.date: 10/16/2018
ms.openlocfilehash: b72d4a8c320ac857fbcd6abe44f467805f72b5b3
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654566"
---
# <a name="strong-naming"></a><span data-ttu-id="e4db2-103">Kesin adlandırma</span><span class="sxs-lookup"><span data-stu-id="e4db2-103">Strong naming</span></span>

<span data-ttu-id="e4db2-104">Tanımlayıcı adlandırma, [tanımlayıcı adlı bir derleme](../assembly/strong-named.md)üreten bir derlemeyi anahtarla imzalamayı ifade eder.</span><span class="sxs-lookup"><span data-stu-id="e4db2-104">Strong naming refers to signing an assembly with a key, producing a [strong-named assembly](../assembly/strong-named.md).</span></span> <span data-ttu-id="e4db2-105">Bir derleme tanımlayıcı olarak adlandırılmışsa, ad ve derleme sürüm numarasına göre benzersiz bir kimlik oluşturur ve derleme çakışmalarını önlemeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4db2-105">When an assembly is strong-named, it creates a unique identity based on the name and assembly version number, and it can help prevent assembly conflicts.</span></span>

<span data-ttu-id="e4db2-106">Güçlü adlandırma için downsıde, derleme tanımlayıcı olarak adlandırılmış olduktan sonra Windows 'daki .NET Framework derlemelerin sıkı şekilde yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4db2-106">The downside to strong naming is that the .NET Framework on Windows enables strict loading of assemblies once an assembly is strong named.</span></span> <span data-ttu-id="e4db2-107">Tanımlayıcı adlı bütünleştirilmiş kod başvurusu, yüklü derlemenin sürümüyle tam olarak eşleşmelidir ve geliştiricilerin derlemeyi kullanırken [bağlama yeniden yönlendirmelerini yapılandırmasına](../../framework/configure-apps/redirect-assembly-versions.md) zorlanır:</span><span class="sxs-lookup"><span data-stu-id="e4db2-107">A strong-named assembly reference must exactly match the version of the loaded assembly, forcing developers to [configure binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) when using the assembly:</span></span>

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

<span data-ttu-id="e4db2-108">.NET geliştiricileri tanımlayıcı adlandırmayla ilgili olarak şikayet edildiğinde, bu durum genellikle ne kadar şikayetçi, katı derleme yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="e4db2-108">When .NET developers complain about strong naming, what they're usually complaining about is strict assembly loading.</span></span> <span data-ttu-id="e4db2-109">Neyse ki, bu sorun .NET Framework yalıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e4db2-109">Fortunately, this issue is isolated to the .NET Framework.</span></span> <span data-ttu-id="e4db2-110">.NET Core, Xamarin, UWP ve diğer birçok .NET uygulaması katı bütünleştirilmiş kod yükleme içermez ve tanımlayıcı adlandırmanın ana alttarafını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e4db2-110">.NET Core, Xamarin, UWP, and most other .NET implementations don't have strict assembly loading and removes the main downside of strong naming.</span></span>

<span data-ttu-id="e4db2-111">Güçlü adlandırmanın önemli bir yönü, bunun viral olması olabilir: tanımlayıcı bir adlandırılmış derleme yalnızca diğer tanımlayıcı adlandırılmış derlemelere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="e4db2-111">One important aspect of strong naming is that it's viral: a strong named assembly can only reference other strong named assemblies.</span></span> <span data-ttu-id="e4db2-112">Kitaplığınız tanımlayıcı olarak adlandırılmazsa, bir uygulama veya kitaplığı oluşturan geliştiricilerin onu kullanarak tanımlayıcı adlandırma yapması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4db2-112">If your library isn't strong named, then you have excluded developers who are building an application or library that needs strong naming from using it.</span></span>

<span data-ttu-id="e4db2-113">Tanımlayıcı adlandırmanın avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e4db2-113">The benefits of strong naming are:</span></span>

1. <span data-ttu-id="e4db2-114">Derlemeye, tanımlayıcı adlı diğer derlemeler tarafından başvurulabilir ve kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4db2-114">The assembly can be referenced and used by other strong-named assemblies.</span></span>
2. <span data-ttu-id="e4db2-115">Derleme, genel derleme önbelleğinde (GAC) depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="e4db2-115">The assembly can be stored in the Global Assembly Cache (GAC).</span></span>
3. <span data-ttu-id="e4db2-116">Derleme diğer derleme sürümleriyle yan yana yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e4db2-116">The assembly can be loaded side by side with other versions of the assembly.</span></span> <span data-ttu-id="e4db2-117">Yan yana derleme yüklemesi, eklenti mimarilerine sahip uygulamalar için yaygın olarak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e4db2-117">Side-by-side assembly loading is commonly required by applications with plug-in architectures.</span></span>

## <a name="create-strong-named-net-libraries"></a><span data-ttu-id="e4db2-118">Tanımlayıcı adlandırılmış .NET kitaplıkları oluşturma</span><span class="sxs-lookup"><span data-stu-id="e4db2-118">Create strong named .NET libraries</span></span>

<span data-ttu-id="e4db2-119">Açık kaynaklı .NET kitaplıklarınızı tanımlayıcı olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="e4db2-119">You should strong name your open-source .NET libraries.</span></span> <span data-ttu-id="e4db2-120">Derlemeyi tanımlayıcı olarak adlandırma, çoğu kişinin bunu kullanmasını sağlar ve katı derleme yükleme yalnızca .NET Framework etkiler.</span><span class="sxs-lookup"><span data-stu-id="e4db2-120">Strong naming an assembly ensures the most people can use it, and strict assembly loading only affects the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="e4db2-121">Bu kılavuz, NuGet.org üzerinde yayımlanan .NET kitaplıkları gibi genel olarak dağıtılmış .NET kitaplıklarına özgüdür. Güçlü adlandırma .NET uygulamaları için gerekli değildir ve varsayılan olarak yapılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e4db2-121">This guidance is specific to publicly distributed .NET libraries, such as .NET libraries published on NuGet.org. Strong naming is not required by most .NET applications and should not be done by default.</span></span>

<span data-ttu-id="e4db2-122">✔️ kitaplığınızın derlemelerinizi tanımlayıcı olarak adlandırmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="e4db2-122">✔️ CONSIDER strong naming your library's assemblies.</span></span>

<span data-ttu-id="e4db2-123">✔️, güçlü adlandırma anahtarını kaynak denetim sisteminize eklemeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="e4db2-123">✔️ CONSIDER adding the strong naming key to your source control system.</span></span>

> <span data-ttu-id="e4db2-124">Genel kullanıma açık bir anahtar, geliştiricilerin kitaplık kaynak kodunuzu aynı anahtarla değiştirmesine ve yeniden derlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e4db2-124">A publicly available key lets developers modify and recompile your library source code with the same key.</span></span>
>
> <span data-ttu-id="e4db2-125">Geçmişte, [kısmi güven senaryolarında](../../framework/misc/using-libraries-from-partially-trusted-code.md)özel izinler vermek için geçmişte kullanılırsa, tanımlayıcı adlandırma anahtarını genel hale kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4db2-125">You shouldn't make the strong naming key public if it has been used in the past to give special permissions in [partial-trust scenarios](../../framework/misc/using-libraries-from-partially-trusted-code.md).</span></span> <span data-ttu-id="e4db2-126">Aksi takdirde, mevcut ortamların güvenliğini tehlikeye atabilir.</span><span class="sxs-lookup"><span data-stu-id="e4db2-126">Otherwise, you might compromise existing environments.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e4db2-127">Kod yayımcısının kimliği isteniyorsa, [Authenticode](/windows-hardware/drivers/install/authenticode) ve [NuGet paket imzalama](/nuget/create-packages/sign-a-package) önerilir.</span><span class="sxs-lookup"><span data-stu-id="e4db2-127">When the identity of the publisher of the code is desired, [Authenticode](/windows-hardware/drivers/install/authenticode) and [NuGet Package Signing](/nuget/create-packages/sign-a-package) are recommended.</span></span> <span data-ttu-id="e4db2-128">Kod erişim güvenliği (CAS) güvenlik azaltma olarak kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e4db2-128">Code Access Security (CAS) should not be used as a security mitigation.</span></span>

<span data-ttu-id="e4db2-129">✔️, kullanıcıların bağlama yeniden yönlendirmelerini azaltmaları ve güncelleştirilme sıklığı hakkında yardım almak için derleme sürümünü yalnızca önemli sürüm değişikliklerinde ARTıRMAYı düşünün.</span><span class="sxs-lookup"><span data-stu-id="e4db2-129">✔️ CONSIDER incrementing the assembly version on only major version changes to help users reduce binding redirects, and how often they're updated.</span></span>

> <span data-ttu-id="e4db2-130">[Sürüm oluşturma ve derleme sürümü](./versioning.md#assembly-version)hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="e4db2-130">Read more about [versioning and the assembly version](./versioning.md#assembly-version).</span></span>

<span data-ttu-id="e4db2-131">❌ Tanımlayıcı adlandırma anahtarını eklemeyin, kaldırmayın veya değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="e4db2-131">❌ DO NOT add, remove, or change the strong naming key.</span></span>

> <span data-ttu-id="e4db2-132">Bir derlemenin tanımlayıcı adlandırma anahtarını değiştirmek derlemenin kimliğini değiştirir ve onu kullanan derlenmiş kodu keser.</span><span class="sxs-lookup"><span data-stu-id="e4db2-132">Modifying an assembly's strong naming key changes the assembly's identity and breaks compiled code that uses it.</span></span> <span data-ttu-id="e4db2-133">Daha fazla bilgi için bkz. [ikili son değişiklikler](./breaking-changes.md#binary-breaking-change).</span><span class="sxs-lookup"><span data-stu-id="e4db2-133">For more information, see [binary breaking changes](./breaking-changes.md#binary-breaking-change).</span></span>

<span data-ttu-id="e4db2-134">❌ Kitaplığınızın güçlü adlandırılmış ve tanımlayıcı olmayan sürümlerini yayımlamayın.</span><span class="sxs-lookup"><span data-stu-id="e4db2-134">❌ DO NOT publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="e4db2-135">Örneğin `Contoso.Api` ve `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="e4db2-135">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

> <span data-ttu-id="e4db2-136">İki paket yayımlandığında geliştirici ekonomik sisteminize çatalın.</span><span class="sxs-lookup"><span data-stu-id="e4db2-136">Publishing two packages forks your developer eco-system.</span></span> <span data-ttu-id="e4db2-137">Ayrıca, her iki pakete bağlı olarak bir uygulama sonlanıyorsa, geliştirici tür adı çakışmaları ile karşılaşabilir.</span><span class="sxs-lookup"><span data-stu-id="e4db2-137">Also, if an application ends up depending on both packages the developer can encounter type name conflicts.</span></span> <span data-ttu-id="e4db2-138">.NET, farklı derlemelerdeki farklı türlerdir.</span><span class="sxs-lookup"><span data-stu-id="e4db2-138">As far as .NET is concerned they are different types in different assemblies.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e4db2-139">[Önceki](cross-platform-targeting.md) 
> [Sonraki](nuget.md)</span><span class="sxs-lookup"><span data-stu-id="e4db2-139">[Previous](cross-platform-targeting.md)
[Next](nuget.md)</span></span>
