---
title: Güçlü adlandırma ve .NET kitaplıkları
description: Güçlü adlandırma .NET kitaplıkları için en iyi uygulama önerileri.
ms.date: 10/16/2018
ms.openlocfilehash: db268093b07a2ece7cdb8329fd789b52da9c5c32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744528"
---
# <a name="strong-naming"></a><span data-ttu-id="8a75d-103">Kesin adlandırma</span><span class="sxs-lookup"><span data-stu-id="8a75d-103">Strong naming</span></span>

<span data-ttu-id="8a75d-104">Güçlü adlandırma, bir derlemeyi anahtarla imzalamayı ve [güçlü adlandırılmış](../assembly/strong-named.md)bir derleme oluşturmayı ifade eder.</span><span class="sxs-lookup"><span data-stu-id="8a75d-104">Strong naming refers to signing an assembly with a key, producing a [strong-named assembly](../assembly/strong-named.md).</span></span> <span data-ttu-id="8a75d-105">Bir derleme güçlü adlandırılmış olduğunda, ad ve derleme sürüm numarasını temel alan benzersiz bir kimlik oluşturur ve derleme çakışmalarını önlemeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a75d-105">When an assembly is strong-named, it creates a unique identity based on the name and assembly version number, and it can help prevent assembly conflicts.</span></span>

<span data-ttu-id="8a75d-106">Güçlü adlandırmanın dezavantajı, Windows'daki .NET Framework'ün, bir derleme güçlü adlandırılmış olduğunda derlemelerin katı yüklenmesine olanak sağlamasıdır.</span><span class="sxs-lookup"><span data-stu-id="8a75d-106">The downside to strong naming is that the .NET Framework on Windows enables strict loading of assemblies once an assembly is strong named.</span></span> <span data-ttu-id="8a75d-107">Güçlü adlandırılmış derleme başvurusu, derleme tarafından başvurulan sürümle tam olarak eşleşmeli ve geliştiricileri derlemeyi kullanırken [bağlama yönlendirmelerini yapılandırmaya](../../framework/configure-apps/redirect-assembly-versions.md) zorlar:</span><span class="sxs-lookup"><span data-stu-id="8a75d-107">A strong-named assembly reference must exactly match the version referenced by an assembly, forcing developers to [configure binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) when using the assembly:</span></span>

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

<span data-ttu-id="8a75d-108">.NET geliştiricileri güçlü adlandırmahakkında şikayette bulunduklarında, genellikle şikayet ettikleri şey sıkı montaj yüklemesidir.</span><span class="sxs-lookup"><span data-stu-id="8a75d-108">When .NET developers complain about strong naming, what they're usually complaining about is strict assembly loading.</span></span> <span data-ttu-id="8a75d-109">Neyse ki, bu sorun .NET Framework için yalıtılır.</span><span class="sxs-lookup"><span data-stu-id="8a75d-109">Fortunately, this issue is isolated to the .NET Framework.</span></span> <span data-ttu-id="8a75d-110">.NET Core, Xamarin, UWP ve diğer birçok .NET uygulamaları sıkı montaj yükleme yok ve güçlü adlandırma ana dezavantajı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8a75d-110">.NET Core, Xamarin, UWP, and most other .NET implementations don't have strict assembly loading and removes the main downside of strong naming.</span></span>

<span data-ttu-id="8a75d-111">Güçlü adlandırma önemli bir yönü viral olmasıdır: güçlü bir adlı derleme sadece diğer güçlü adlı derlemeler referans olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a75d-111">One important aspect of strong naming is that it's viral: a strong named assembly can only reference other strong named assemblies.</span></span> <span data-ttu-id="8a75d-112">Kitaplığınız güçlü adlandırılmış değilse, güçlü adlandırılması gereken bir uygulama veya kitaplık oluşturan geliştiricileri hariç tardınız.</span><span class="sxs-lookup"><span data-stu-id="8a75d-112">If your library isn't strong named, then you have excluded developers who are building an application or library that needs strong naming from using it.</span></span>

<span data-ttu-id="8a75d-113">Güçlü adlandırmanın yararları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8a75d-113">The benefits of strong naming are:</span></span>

1. <span data-ttu-id="8a75d-114">Derleme başvurulabilir ve diğer güçlü adlı derlemeler tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8a75d-114">The assembly can be referenced and used by other strong-named assemblies.</span></span>
2. <span data-ttu-id="8a75d-115">Derleme, Genel Montaj Önbelleğinde (GAC) depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="8a75d-115">The assembly can be stored in the Global Assembly Cache (GAC).</span></span>
3. <span data-ttu-id="8a75d-116">Montaj, derlemenin diğer sürümleriyle yan yana yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8a75d-116">The assembly can be loaded side by side with other versions of the assembly.</span></span> <span data-ttu-id="8a75d-117">Yan yana montaj yüklemegenellikle eklenti mimarileri ile uygulamalar tarafından gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8a75d-117">Side-by-side assembly loading is commonly required by applications with plug-in architectures.</span></span>

## <a name="create-strong-named-net-libraries"></a><span data-ttu-id="8a75d-118">Güçlü adlı .NET kitaplıkları oluşturma</span><span class="sxs-lookup"><span data-stu-id="8a75d-118">Create strong named .NET libraries</span></span>

<span data-ttu-id="8a75d-119">Açık kaynak kodlu .NET kitaplıklarınızı güçlü bir şekilde adlandırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8a75d-119">You should strong name your open-source .NET libraries.</span></span> <span data-ttu-id="8a75d-120">Bir derlemeyi güçlü adlandırma, çoğu kişinin onu kullanabileceğini ve sıkı derleme yüklemesinin yalnızca .NET Framework'üni etkilemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a75d-120">Strong naming an assembly ensures the most people can use it, and strict assembly loading only affects the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="8a75d-121">Bu kılavuz, NuGet.org'da yayınlanan .NET kitaplıkları gibi herkese açık olarak dağıtılan .NET kitaplıklarına özgüdür. Güçlü adlandırma çoğu .NET uygulamaları tarafından gerekli değildir ve varsayılan olarak yapılmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a75d-121">This guidance is specific to publicly distributed .NET libraries, such as .NET libraries published on NuGet.org. Strong naming is not required by most .NET applications and should not be done by default.</span></span>

<span data-ttu-id="8a75d-122">✔️ kitaplığınızın derlemelerine güçlü bir isim vermeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="8a75d-122">✔️ CONSIDER strong naming your library's assemblies.</span></span>

<span data-ttu-id="8a75d-123">✔️ kaynak denetim sisteminize güçlü adlandırma anahtarı eklemeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="8a75d-123">✔️ CONSIDER adding the strong naming key to your source control system.</span></span>

> <span data-ttu-id="8a75d-124">Genel kullanıma açık bir anahtar, geliştiricilerin kitaplık kaynak kodunuzu aynı anahtarla değiştirmesine ve yeniden derlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a75d-124">A publicly available key lets developers modify and recompile your library source code with the same key.</span></span>
>
> <span data-ttu-id="8a75d-125">Geçmişte [kısmi güven senaryolarında](../../framework/misc/using-libraries-from-partially-trusted-code.md)özel izinler vermek için kullanılmışsa, güçlü adlandırma anahtarını herkese açık hale getirmemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a75d-125">You shouldn't make the strong naming key public if it has been used in the past to give special permissions in [partial-trust scenarios](../../framework/misc/using-libraries-from-partially-trusted-code.md).</span></span> <span data-ttu-id="8a75d-126">Aksi takdirde, varolan ortamları tehlikeye atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a75d-126">Otherwise, you might compromise existing environments.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a75d-127">Kodun yayımcısının kimliği istendiğinde, [Authenticode](/windows-hardware/drivers/install/authenticode) ve [NuGet Paket İmzalama](/nuget/create-packages/sign-a-package) önerilir.</span><span class="sxs-lookup"><span data-stu-id="8a75d-127">When the identity of the publisher of the code is desired, [Authenticode](/windows-hardware/drivers/install/authenticode) and [NuGet Package Signing](/nuget/create-packages/sign-a-package) are recommended.</span></span> <span data-ttu-id="8a75d-128">Kod Erişim Güvenliği (CAS) güvenlik azaltma olarak kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a75d-128">Code Access Security (CAS) should not be used as a security mitigation.</span></span>

<span data-ttu-id="8a75d-129">✔️ kullanıcıların bağlama yönlendirmelerini ve ne sıklıkta güncelleştirildiklerini azaltmalarına yardımcı olmak için yalnızca ana sürüm değişikliklerinde derleme sürümünü niçin artımlı olarak düşünün.</span><span class="sxs-lookup"><span data-stu-id="8a75d-129">✔️ CONSIDER incrementing the assembly version on only major version changes to help users reduce binding redirects, and how often they're updated.</span></span>

> <span data-ttu-id="8a75d-130">[Sürüm ve derleme sürümü](./versioning.md#assembly-version)hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="8a75d-130">Read more about [versioning and the assembly version](./versioning.md#assembly-version).</span></span>

<span data-ttu-id="8a75d-131">❌Güçlü adlandırma anahtarını eklemeYIN, kaldırmayın veya değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="8a75d-131">❌ DO NOT add, remove, or change the strong naming key.</span></span>

> <span data-ttu-id="8a75d-132">Bir derlemenin güçlü adlandırma anahtarını değiştirmek, derlemenin kimliğini değiştirir ve onu kullanan derlenmiş kodu kırar.</span><span class="sxs-lookup"><span data-stu-id="8a75d-132">Modifying an assembly's strong naming key changes the assembly's identity and breaks compiled code that uses it.</span></span> <span data-ttu-id="8a75d-133">Daha fazla bilgi için [ikili kesme değişikliklerine](./breaking-changes.md#binary-breaking-change)bakın.</span><span class="sxs-lookup"><span data-stu-id="8a75d-133">For more information, see [binary breaking changes](./breaking-changes.md#binary-breaking-change).</span></span>

<span data-ttu-id="8a75d-134">❌Kitaplığınızın güçlü adlandırılmış ve güçlü olmayan adlandırılmış sürümlerini yayımlamayın.</span><span class="sxs-lookup"><span data-stu-id="8a75d-134">❌ DO NOT publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="8a75d-135">Örneğin, `Contoso.Api` ve `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="8a75d-135">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

> <span data-ttu-id="8a75d-136">İki paket yayınlamak geliştirici eko-sisteminizi çatallar.</span><span class="sxs-lookup"><span data-stu-id="8a75d-136">Publishing two packages forks your developer eco-system.</span></span> <span data-ttu-id="8a75d-137">Ayrıca, bir uygulama her iki pakete bağlı olarak biterse geliştirici tür adı çakışmaları karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a75d-137">Also, if an application ends up depending on both packages the developer can encounter type name conflicts.</span></span> <span data-ttu-id="8a75d-138">.NET'e göre farklı derlemelerde farklı türlerdedirler.</span><span class="sxs-lookup"><span data-stu-id="8a75d-138">As far as .NET is concerned they are different types in different assemblies.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8a75d-139">[Önceki](cross-platform-targeting.md)
>[Sonraki](nuget.md)</span><span class="sxs-lookup"><span data-stu-id="8a75d-139">[Previous](cross-platform-targeting.md)
[Next](nuget.md)</span></span>
