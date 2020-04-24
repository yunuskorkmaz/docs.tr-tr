---
title: C# Versioning - C# Kılavuzu
description: C# ve .NET'te sürümlemenin nasıl çalıştığını anlama
ms.date: 01/08/2017
ms.technology: csharp-advanced-concepts
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: dc192337e4eaa5f9f1d6509ea8c15deeac34a48c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645462"
---
# <a name="versioning-in-c"></a><span data-ttu-id="db95d-103">C sürümü\#</span><span class="sxs-lookup"><span data-stu-id="db95d-103">Versioning in C\#</span></span>

<span data-ttu-id="db95d-104">Bu eğitimde .NET'te sürümlemenin ne anlama geldiğini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="db95d-104">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="db95d-105">Ayrıca kitaplığınızı sürüm yaparken ve kitaplığın yeni bir sürümüne yükseltme yaparken göz önünde bulundurmanız gereken faktörleri de öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="db95d-105">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="db95d-106">Kitaplık Yazma</span><span class="sxs-lookup"><span data-stu-id="db95d-106">Authoring Libraries</span></span>

<span data-ttu-id="db95d-107">Genel kullanım için .NET kitaplıkları oluşturmuş bir geliştirici olarak, büyük olasılıkla yeni güncelleştirmeler sunması gereken durumlarda bulunuyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="db95d-107">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="db95d-108">Varolan kodun kitaplığınuzun yeni sürümüne sorunsuz bir şekilde geçiş olduğundan emin olmak için bu işlemi nasıl gerçekleştirebilirsiniz çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="db95d-108">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="db95d-109">Yeni bir sürüm oluştururken göz önünde bulundurulması gereken birkaç şey şunlardır:</span><span class="sxs-lookup"><span data-stu-id="db95d-109">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="db95d-110">Anlamsal Versiyon</span><span class="sxs-lookup"><span data-stu-id="db95d-110">Semantic Versioning</span></span>

<span data-ttu-id="db95d-111">[Anlamsal sürüm](https://semver.org/) (kısaca SemVer), belirli kilometre taşı olaylarını belirtmek için kitaplığınızın sürümlerine uygulanan bir adlandırma kuralıdır.</span><span class="sxs-lookup"><span data-stu-id="db95d-111">[Semantic versioning](https://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="db95d-112">İdeal olarak, kitaplığınıza verdiğiniz sürüm bilgileri, geliştiricilerin aynı kitaplığın eski sürümlerinden yararlanan projeleriile uyumluluğu belirlemelerine yardımcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db95d-112">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="db95d-113">SemVer için en temel yaklaşım 3 `MAJOR.MINOR.PATCH`bileşen biçimi, nerede:</span><span class="sxs-lookup"><span data-stu-id="db95d-113">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>

- <span data-ttu-id="db95d-114">`MAJOR`uyumsuz API değişiklikleri yaptığınızda artımlı</span><span class="sxs-lookup"><span data-stu-id="db95d-114">`MAJOR` is incremented when you make incompatible API changes</span></span>
- <span data-ttu-id="db95d-115">`MINOR`işlevselliği geriye doğru uyumlu bir şekilde eklediğinizde artırılır</span><span class="sxs-lookup"><span data-stu-id="db95d-115">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
- <span data-ttu-id="db95d-116">`PATCH`geriye uyumlu hata düzeltmeleri yaptığınızda artımlı</span><span class="sxs-lookup"><span data-stu-id="db95d-116">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="db95d-117">.NET kitaplığınıza sürüm bilgilerini uygularken ön sürüm sürümleri vb. gibi diğer senaryoları belirtmenin yolları da vardır.</span><span class="sxs-lookup"><span data-stu-id="db95d-117">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="db95d-118">Geriye Dönük Uyumluluk</span><span class="sxs-lookup"><span data-stu-id="db95d-118">Backwards Compatibility</span></span>

<span data-ttu-id="db95d-119">Kitaplığınızın yeni sürümlerini serbest bıraktırken, önceki sürümlerle geriye dönük uyumluluk büyük olasılıkla başlıca endişelerinizden biri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="db95d-119">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="db95d-120">Kitaplığınız yeni bir sürümü kaynak önceki sürüme bağlı kod, yeniden derlendiğinde, yeni sürümü ile çalışabilir bağlı ise ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="db95d-120">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span>
<span data-ttu-id="db95d-121">Eski sürüme bağlı bir uygulama, yeniden derleme olmadan yeni sürümle çalışabiliyorsa, kitaplığınızın yeni bir sürümü ikili uyumludur.</span><span class="sxs-lookup"><span data-stu-id="db95d-121">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="db95d-122">Kitaplığınızın eski sürümleriyle geriye doğru uyumluluğu korumaya çalışırken göz önünde bulundurmanız gereken bazı şeyler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="db95d-122">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

- <span data-ttu-id="db95d-123">Sanal yöntemler: Yeni sürümde sanal olmayan bir sanal yöntem yaptığınızda, bu yöntemi geçersiz kılan projelerin güncellenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="db95d-123">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="db95d-124">Bu büyük bir kırılma değişim ve şiddetle cesareti olduğunu.</span><span class="sxs-lookup"><span data-stu-id="db95d-124">This is a huge breaking change and is strongly discouraged.</span></span>
- <span data-ttu-id="db95d-125">Yöntem imzaları: Bir yöntem davranışını güncelleştirmek imzasını da değiştirmenizi gerektiriyorsa, bunun yerine, bu yönteme çağıran kodun çalışmaya devam etmesi için aşırı yükleme oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="db95d-125">Method signatures: When updating a method behavior requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="db95d-126">Uygulamanın tutarlı kalması için eski yöntem imzasını her zaman yeni yöntem imzasına çağırmak için değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db95d-126">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
- <span data-ttu-id="db95d-127">[Eski öznitelik](language-reference/attributes/general.md#obsolete-attribute): Bu özniteliği, amortismana kaldırılmış ve gelecek sürümlerde kaldırılma olasılığı olan sınıfları veya sınıf üyelerini belirtmek için kodunuzdaki bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db95d-127">[Obsolete attribute](language-reference/attributes/general.md#obsolete-attribute): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span> <span data-ttu-id="db95d-128">Bu, kitaplığınızı kullanan geliştiricilerin değişiklikleri kırmaya daha iyi hazır olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="db95d-128">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
- <span data-ttu-id="db95d-129">İsteğe Bağlı Yöntem Bağımsız Değişkenleri: Daha önce isteğe bağlı yöntem bağımsız değişkenlerini zorunlu hale getirdiğinizde veya varsayılan değerlerini değiştirdiğinizde, bu bağımsız değişkenleri sağlamayan tüm kodun güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="db95d-129">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>

> [!NOTE]
> <span data-ttu-id="db95d-130">Zorunlu bağımsız değişkenleri isteğe bağlı hale getirmek, özellikle yöntemin davranışını değiştirmezse çok az etkiye sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db95d-130">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behavior.</span></span>

<span data-ttu-id="db95d-131">Kullanıcılarınızın kitaplığınızın yeni sürümüne yükseltmesini ne kadar kolay hale getirirseniz, daha erken yükseltme yapma olasılıkları o kadar artar.</span><span class="sxs-lookup"><span data-stu-id="db95d-131">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="db95d-132">Uygulama Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="db95d-132">Application Configuration File</span></span>

<span data-ttu-id="db95d-133">Bir .NET geliştiricisi olarak, çoğu proje türünde [dosya `app.config` ](../framework/configure-apps/file-schema/index.md) nın bulunma olasılığı çok yüksektür.</span><span class="sxs-lookup"><span data-stu-id="db95d-133">As a .NET developer there's a very high chance you've encountered [the `app.config` file](../framework/configure-apps/file-schema/index.md) present in most project types.</span></span>
<span data-ttu-id="db95d-134">Bu basit yapılandırma dosyası, yeni güncelleştirmelerin kullanıma sunulmasını iyileştirmek için uzun bir yol kat edebilir.</span><span class="sxs-lookup"><span data-stu-id="db95d-134">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="db95d-135">Kitaplıklarınızı genellikle düzenli olarak değişmesi muhtemel bilgilerin `app.config` dosyada depolanacak şekilde tasarlamanız gerekir, bu şekilde bu tür bilgiler güncelleştirildiğinde, eski sürümlerin config dosyasının kitaplığın yeniden derlenmesine gerek kalmadan yenisiyle değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="db95d-135">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated, the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="db95d-136">Tüketen Kütüphaneler</span><span class="sxs-lookup"><span data-stu-id="db95d-136">Consuming Libraries</span></span>

<span data-ttu-id="db95d-137">Diğer geliştiriciler tarafından oluşturulmuş .NET kitaplıklarını tüketen bir geliştirici olarak, büyük olasılıkla kitaplığın yeni bir sürümünün projenizle tam olarak uyumlu olmayabileceğinin farkındasınızdır ve genellikle bu değişikliklerle çalışmak için kodunuzu güncelleştirmek zorunda kalacaksınız.</span><span class="sxs-lookup"><span data-stu-id="db95d-137">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="db95d-138">Şanslısınız ki, C# ve .NET ekosistemi, çığır açan değişikliklere neden olabilecek kitaplıkların yeni sürümleriyle çalışmak üzere uygulamamızı kolayca güncellememize olanak tanıyan özellikler ve tekniklerle birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="db95d-138">Lucky for you, C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="db95d-139">Derleme Bağlama Yeniden Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="db95d-139">Assembly Binding Redirection</span></span>

<span data-ttu-id="db95d-140">Uygulamanızın kullandığı kitaplığın sürümünü güncelleştirmek için *app.config* dosyasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db95d-140">You can use the *app.config* file to update the version of a library your app uses.</span></span> <span data-ttu-id="db95d-141">[*Bağlayıcı yönlendirme*](../framework/configure-apps/redirect-assembly-versions.md)olarak adlandırılan bir yönlendirme ekleyerek, uygulamanızı yeniden derlemek zorunda kalmadan yeni kitaplık sürümünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db95d-141">By adding what is called a [*binding redirect*](../framework/configure-apps/redirect-assembly-versions.md), you can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="db95d-142">Aşağıdaki örnek, uygulamanızın *app.config* dosyasını ilk derlenen `1.0.1` `1.0.0` sürümüyerine `ReferencedLibrary` yama sürümünü kullanmak üzere nasıl güncelleştireceğinizgösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="db95d-142">The following example shows how you would update your app's *app.config* file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="db95d-143">Bu yaklaşım yalnızca yeni sürümü `ReferencedLibrary` uygulamanızla ikili olarak uyumluysa çalışır.</span><span class="sxs-lookup"><span data-stu-id="db95d-143">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="db95d-144">Uyumluluğu belirlerken dikkat etmesi gereken değişiklikler için yukarıdaki [Geriye Dönük Uyumluluk](#backwards-compatibility) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="db95d-144">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="db95d-145">new</span><span class="sxs-lookup"><span data-stu-id="db95d-145">new</span></span>

<span data-ttu-id="db95d-146">Bir taban `new` sınıfın devralınan üyelerini gizlemek için değiştirici kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="db95d-146">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="db95d-147">Bu, türetilmiş sınıfların temel sınıflardaki güncelleştirmelere yanıt verebileceği yollardan biridir.</span><span class="sxs-lookup"><span data-stu-id="db95d-147">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="db95d-148">Aşağıdaki örneği ele alalım:</span><span class="sxs-lookup"><span data-stu-id="db95d-148">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](~/samples/snippets/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="db95d-149">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="db95d-149">**Output**</span></span>

```console
A base method
A derived method
```

<span data-ttu-id="db95d-150">Yukarıdaki örnekten, 'de `DerivedClass` `BaseClass`bulunan `MyMethod` yöntemi nasıl gizlediğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db95d-150">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="db95d-151">Bu, kitaplığın yeni sürümündeki bir taban sınıf, türemiş sınıfınızda zaten var olan `new` bir üye eklendiğinde, taban sınıf üyesini gizlemek için türemiş sınıf üyenizdeki değiştiriciyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db95d-151">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="db95d-152">Değiştirici `new` belirtilmediğinde, türetilmiş bir sınıf varsayılan olarak bir taban sınıfta çakışan üyeleri gizler, ancak derleyici uyarısı oluşturulacak olsa da kod yine de derlenir.</span><span class="sxs-lookup"><span data-stu-id="db95d-152">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="db95d-153">Bu, yalnızca varolan bir sınıfa yeni üyeler eklemenin, kitaplığınızın yeni sürümünü hem kaynak hem de ikili olarak bağlı olan kodla uyumlu hale getirir.</span><span class="sxs-lookup"><span data-stu-id="db95d-153">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="db95d-154">override</span><span class="sxs-lookup"><span data-stu-id="db95d-154">override</span></span>

<span data-ttu-id="db95d-155">Değiştirici, `override` türetilmiş bir uygulamanın, bir taban sınıf üyesinin uygulanmasını gizlemek yerine genişletir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="db95d-155">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="db95d-156">Taban sınıf üyesinin değiştiricinin `virtual` bu uygulamaya uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="db95d-156">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/snippets/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="db95d-157">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="db95d-157">**Output**</span></span>

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="db95d-158">`override` Değiştirici derleme zamanında değerlendirilir ve derleyici geçersiz kılacak sanal bir üye bulamazsa hata atar.</span><span class="sxs-lookup"><span data-stu-id="db95d-158">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="db95d-159">Tartışılan teknikler hakkındaki bilginiz ve bunları kullanacağınız durumlar hakkındaki anlayışınız, bir kütüphanenin sürümleri arasındaki geçişi kolaylaştırmaya yönelik uzun bir yol kat edecektir.</span><span class="sxs-lookup"><span data-stu-id="db95d-159">Your knowledge of the discussed techniques and your understanding of the situations in which to use them, will go a long way towards easing the transition between versions of a library.</span></span>
