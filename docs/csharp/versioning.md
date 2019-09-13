---
title: C#Sürüm oluşturma C# -kılavuz
description: Sürüm oluşturma 'nın ve .NET C# 'te nasıl çalıştığını anlama
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: bfad7abe6b2b5c6a19324656963a79212a317110
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926588"
---
# <a name="versioning-in-c"></a><span data-ttu-id="5bd9d-103">C 'de sürüm oluşturma\#</span><span class="sxs-lookup"><span data-stu-id="5bd9d-103">Versioning in C\#</span></span>

<span data-ttu-id="5bd9d-104">Bu öğreticide .NET 'teki sürüm oluşturmanın ne anlama geldiğini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-104">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="5bd9d-105">Ayrıca, kitaplığınızın sürümü oluşturulurken göz önünde bulundurmanız gereken faktörleri ve yeni bir kitaplık sürümüne yükseltmeyi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-105">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="5bd9d-106">Yazma kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="5bd9d-106">Authoring Libraries</span></span>

<span data-ttu-id="5bd9d-107">Genel kullanım için .NET kitaplıkları oluşturmuş olan bir geliştirici olarak, büyük olasılıkla yeni güncelleştirmeleri almanız gereken durumlarda olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-107">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="5bd9d-108">Bu süreç hakkında daha fazla bilgi için, var olan kodun kitaplığınızın yeni sürümüne sorunsuz bir şekilde geçişini sağlamak için ihtiyacınız olduğu için çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-108">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="5bd9d-109">Yeni bir sürüm oluştururken göz önünde bulundurmanız gereken birkaç nokta vardır:</span><span class="sxs-lookup"><span data-stu-id="5bd9d-109">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="5bd9d-110">Anlamsal sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="5bd9d-110">Semantic Versioning</span></span>

<span data-ttu-id="5bd9d-111">[Anlamsal sürüm oluşturma](https://semver.org/) (Short için SemVer), belirli kilometre taşı olaylarını belirtmek için kitaplığınızın sürümlerine uygulanan bir adlandırma kuralıdır.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-111">[Semantic versioning](https://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="5bd9d-112">İdeal olarak, kitaplığınıza verdiğiniz sürüm bilgileri, geliştiricilerin, aynı kitaplığın eski sürümlerini kullanan projelerle uyumluluğunu belirlemesine yardımcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-112">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="5bd9d-113">Semver 'e en temel yaklaşım, burada 3 bileşen biçimidir `MAJOR.MINOR.PATCH`:</span><span class="sxs-lookup"><span data-stu-id="5bd9d-113">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>

* <span data-ttu-id="5bd9d-114">`MAJOR`uyumsuz API değişiklikleri yaptığınızda artırılır</span><span class="sxs-lookup"><span data-stu-id="5bd9d-114">`MAJOR` is incremented when you make incompatible API changes</span></span>
* <span data-ttu-id="5bd9d-115">`MINOR`işlevselliği geriye dönük olarak uyumlu bir şekilde eklediğinizde artırılır</span><span class="sxs-lookup"><span data-stu-id="5bd9d-115">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
* <span data-ttu-id="5bd9d-116">`PATCH`, geriye dönük olarak uyumlu hata düzeltmeleri yaptığınızda artırılır</span><span class="sxs-lookup"><span data-stu-id="5bd9d-116">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="5bd9d-117">Sürüm bilgilerini .NET kitaplığınıza uygularken yayın öncesi sürümler gibi başka senaryolar da belirtmek için de çeşitli yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-117">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="5bd9d-118">Geriye dönük uyumluluk</span><span class="sxs-lookup"><span data-stu-id="5bd9d-118">Backwards Compatibility</span></span>

<span data-ttu-id="5bd9d-119">Kitaplığınızın yeni sürümlerini serbest bırakmakta önceki sürümlerle geriye dönük uyumluluk, büyük ihtimalle önemli kaygılardan biri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-119">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="5bd9d-120">Önceki sürüme bağımlı olan kodun yeniden derlenmesi sırasında, yeni sürümle birlikte çalışarak kitaplığınızın yeni bir sürümü önceki bir sürümle kaynak uyumludur.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-120">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span> <span data-ttu-id="5bd9d-121">Eski sürüme bağımlı bir uygulama, yeniden derleme olmadan yeni sürümle birlikte çalışarak kitaplığınızın yeni bir sürümü ikili uyumludur.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-121">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="5bd9d-122">Kitaplığınızın eski sürümleriyle geriye dönük uyumluluğu sürdürmeye çalışırken göz önünde bulundurmanız gereken bazı noktalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5bd9d-122">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

* <span data-ttu-id="5bd9d-123">Sanal Yöntemler: Yeni sürümünüzde sanal olmayan bir sanal yöntem yaptığınızda, bu yöntemi geçersiz kılan projelerin güncelleştirilmesini sağlamak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-123">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="5bd9d-124">Bu çok büyük bir değişiklik ve kesinlikle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-124">This is a huge breaking change and is strongly discouraged.</span></span>
* <span data-ttu-id="5bd9d-125">Yöntem imzaları: Bir yöntem davranışını güncelleştirirken, onun imzasını da değiştirmeniz gerekir, bunun yerine bu yönteme çağrı yapan kodun çalışmaya devam etmesi için bir aşırı yükleme oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-125">Method signatures: When updating a method behaviour requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="5bd9d-126">Uygulamanın tutarlı kalması için yeni yöntem imzasını çağırmak üzere, eski yöntem imzasını her zaman değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-126">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
* <span data-ttu-id="5bd9d-127">[Eski öznitelik](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Bu özniteliği kodunuzda bu özniteliği kullanarak kullanım dışı olan sınıfları veya sınıf üyelerini, gelecekteki sürümlerde de kaldırılmasını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-127">[Obsolete attribute](programming-guide/concepts/attributes/common-attributes.md#Obsolete): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span> <span data-ttu-id="5bd9d-128">Bu, kitaplığınızı kullanan geliştiricilerin, son değişiklikler için daha iyi hazırlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-128">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
* <span data-ttu-id="5bd9d-129">İsteğe bağlı yöntem bağımsız değişkenleri: Daha önce isteğe bağlı yöntem bağımsız değişkenlerini zorunlu yaptığınızda veya varsayılan değerlerini değiştirirseniz, bu bağımsız değişkenleri sağlamadan tüm kodun güncellenmesi gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-129">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>

> [!NOTE]
> <span data-ttu-id="5bd9d-130">Zorunlu bağımsız değişkenleri isteğe bağlı hale getirmek, özellikle yöntemin davranışını değiştirmiyorsa çok az etkiye sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-130">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behaviour.</span></span>

<span data-ttu-id="5bd9d-131">Kullanıcılarınızın kitaplığınızın yeni sürümüne yükseltme yapmasını kolaylaştırır, daha önce yükseltebilecekleri büyük olasılıkla daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-131">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="5bd9d-132">Uygulama yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="5bd9d-132">Application Configuration File</span></span>

<span data-ttu-id="5bd9d-133">Bir .net geliştiricisi olarak çoğu proje türünde mevcut olan [ `app.config` dosyayla](../framework/configure-apps/file-schema/index.md) karşılaşmanız çok yüksek bir şansınız vardır.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-133">As a .NET developer there's a very high chance you've encountered [the `app.config` file](../framework/configure-apps/file-schema/index.md) present in most project types.</span></span>
<span data-ttu-id="5bd9d-134">Bu basit yapılandırma dosyası, yeni güncelleştirmelerin dağıtımını iyileştirmek için uzun bir yönteme gidebilirler.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-134">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="5bd9d-135">Genellikle kitaplıklarınızı düzenli olarak değişen bilgiler `app.config` dosyada depolandığından, bu şekilde, bu bilgilerin daha eski sürümlerin yapılandırma dosyası güncelleştiriliyorsa yalnızca yeni bir sürüm ile değiştirilmeleri gerekir. Kitaplığı yeniden derlemek zorunda kalmadan.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-135">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="5bd9d-136">Kitaplıkları kullanma</span><span class="sxs-lookup"><span data-stu-id="5bd9d-136">Consuming Libraries</span></span>

<span data-ttu-id="5bd9d-137">Diğer geliştiriciler tarafından oluşturulan .NET kitaplıklarını tüketen bir geliştirici olarak, bir kitaplığın yeni bir sürümünün projenizle tamamen uyumlu olabileceğini ve genellikle kendi kodunuzu bu değişikliklerle çalışacak şekilde güncelleştirmek zorunda olduğunu fark edersiniz.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-137">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="5bd9d-138">Sizin C# için Lucky ve .net ekosistemi, uygulamamızı, son değişiklikleri ortaya çıkaracak yeni kitaplıkların sürümleriyle çalışacak şekilde kolayca güncelleştirmenize imkan tanıyan özellikler ve teknikler sunar.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-138">Lucky for you C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="5bd9d-139">Derleme bağlama yeniden yönlendirmesi</span><span class="sxs-lookup"><span data-stu-id="5bd9d-139">Assembly Binding Redirection</span></span>

<span data-ttu-id="5bd9d-140">Uygulamanızın kullandığı bir kitaplığın `app.config` sürümünü güncelleştirmek için dosyasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-140">You can use the `app.config` file to update the version of a library your app uses.</span></span> <span data-ttu-id="5bd9d-141">[*Bağlama yeniden yönlendirme*](../framework/configure-apps/redirect-assembly-versions.md) olarak adlandırılan öğesine ekleyerek, uygulamanızı yeniden derlemek zorunda kalmadan yeni kitaplık sürümünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-141">By adding what is called a [*binding redirect*](../framework/configure-apps/redirect-assembly-versions.md) you can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="5bd9d-142">Aşağıdaki örnek, uygulamasının ilk `app.config` olarak derlenmiş `1.0.0` sürümü `ReferencedLibrary` yerine `1.0.1` düzeltme eki sürümünü kullanmak için uygulamanızın dosyasını nasıl güncelleşbileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-142">The following example shows how you would update your app's `app.config` file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="5bd9d-143">Bu yaklaşım, yalnızca yeni sürümü `ReferencedLibrary` uygulamanız ile uyumluysa çalışır.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-143">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="5bd9d-144">Uyumluluk belirlenirken yapılan değişiklikler için yukarıdaki [geriye dönük uyumluluk](#backwards-compatibility) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-144">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="5bd9d-145">new</span><span class="sxs-lookup"><span data-stu-id="5bd9d-145">new</span></span>

<span data-ttu-id="5bd9d-146">Bir temel sınıfın `new` devralınan üyelerini gizlemek için değiştiricisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-146">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="5bd9d-147">Bu, türetilmiş sınıfların temel sınıflarda güncelleştirmelere yanıt verebildiği bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-147">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="5bd9d-148">Aşağıdaki örneği uygulayın:</span><span class="sxs-lookup"><span data-stu-id="5bd9d-148">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="5bd9d-149">**Output**</span><span class="sxs-lookup"><span data-stu-id="5bd9d-149">**Output**</span></span>

```
A base method
A derived method
```

<span data-ttu-id="5bd9d-150">Yukarıdaki örnekte, ' de `DerivedClass` `BaseClass`bulunan `MyMethod` yöntemin nasıl gizlediğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-150">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="5bd9d-151">Bu, bir kitaplığın yeni sürümündeki bir temel sınıf, türetilmiş sınıfınıza zaten mevcut olan bir üyeyi eklediğinde, taban sınıf üyesini gizlemek için yalnızca türetilmiş sınıf üyeinizdeki `new` değiştiriciyi kullanmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-151">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="5bd9d-152">`new` Değiştirici belirtilmediğinde, türetilmiş bir sınıf varsayılan olarak bir temel sınıfta çakışan üyeleri gizleyecek, ancak derleyici uyarısı üretilse de kod derlenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-152">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="5bd9d-153">Bu, yalnızca varolan bir sınıfa yeni üye eklemek, kitaplığınızın bu yeni sürümünün hem kaynak hem de ikilinin buna bağlı kodla uyumlu olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-153">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="5bd9d-154">override</span><span class="sxs-lookup"><span data-stu-id="5bd9d-154">override</span></span>

<span data-ttu-id="5bd9d-155">`override` Değiştirici türetilmiş bir uygulamanın, bir temel sınıf üyesinin uygulamasını gizliyor yerine genişlettiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-155">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="5bd9d-156">Temel sınıf üyesine `virtual` değiştiriciye uygulanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-156">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="5bd9d-157">**Output**</span><span class="sxs-lookup"><span data-stu-id="5bd9d-157">**Output**</span></span>

```
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="5bd9d-158">`override` Değiştirici derleme zamanında değerlendirilir ve geçersiz kılmak için bir sanal üye bulamazsa derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-158">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="5bd9d-159">Ele alınan tekniklerin ve bunların hangi durumlardan hangilerinin kullanılacağını kavramanız, bir kitaplığın sürümleri arasında geçiş kolaylığı hızını artırmak için uzun bir yönteme gidecektir.</span><span class="sxs-lookup"><span data-stu-id="5bd9d-159">Your knowledge of the discussed techniques as well as your understanding of what situations to use them will go a long way to boost the ease of transition between versions of a library.</span></span>
 