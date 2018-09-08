---
title: C# sürüm oluşturma - C# Kılavuzu
description: Sürüm oluşturma, C# ve .NET dillerinde nasıl çalıştığını anlamak
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 949b7414116169cada62b48392f37809f26d7ff9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185764"
---
# <a name="versioning-in-c"></a><span data-ttu-id="447cf-103">C# sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="447cf-103">Versioning in C#</span></span> #

<span data-ttu-id="447cf-104">Bu öğreticide, hangi sürüm anlamına gelir. NET'te öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="447cf-104">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="447cf-105">Dikkat edilecek Etkenler da öğreneceksiniz sürüm kitaplığınızı yanı sıra yeni bir sürümüne yükseltme bir kitaplık.</span><span class="sxs-lookup"><span data-stu-id="447cf-105">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of the a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="447cf-106">Geliştirme kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="447cf-106">Authoring Libraries</span></span>

<span data-ttu-id="447cf-107">Genel kullanım için .NET kitaplıklarını oluşturan bir geliştirici olarak, seçtiğiniz en yeni güncelleştirmeleri almak için sahip olduğu durumlarda büyük olasılıkla bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="447cf-107">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="447cf-108">Sorunsuz geçiş kitaplığınızın yeni sürümü için mevcut kod olduğundan emin olmak gereken bu işlem hakkında nasıl gittiğiniz çok önemli.</span><span class="sxs-lookup"><span data-stu-id="447cf-108">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="447cf-109">Yeni bir yayın oluştururken dikkate alınması gereken birkaç nokta şunlardır:</span><span class="sxs-lookup"><span data-stu-id="447cf-109">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="447cf-110">Semantic Versioning</span><span class="sxs-lookup"><span data-stu-id="447cf-110">Semantic Versioning</span></span>

<span data-ttu-id="447cf-111">[Semantic versioning](http://semver.org/) olduğu belirli aşama olayları belirtmek için kitaplık sürümleri için uygulanan bir adlandırma kuralı (kısaca SemVer).</span><span class="sxs-lookup"><span data-stu-id="447cf-111">[Semantic versioning](http://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="447cf-112">Kitaplığınızı size sürüm bilgilerini geliştiriciler bu eski sürümleri aynı kullanan projelerini uyumluluğunu belirlemek ideal olarak, yardımcı kitaplık.</span><span class="sxs-lookup"><span data-stu-id="447cf-112">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="447cf-113">En temel SemVer 3 bileşeni biçimi yaklaşımdır `MAJOR.MINOR.PATCH`burada:</span><span class="sxs-lookup"><span data-stu-id="447cf-113">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>

* <span data-ttu-id="447cf-114">`MAJOR` uyumsuz API değişiklik yaptığınızda artırılır</span><span class="sxs-lookup"><span data-stu-id="447cf-114">`MAJOR` is incremented when you make incompatible API changes</span></span>
* <span data-ttu-id="447cf-115">`MINOR` Geriye dönük uyumlu bir biçimde işlevselliği eklediğinizde artırılır</span><span class="sxs-lookup"><span data-stu-id="447cf-115">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
* <span data-ttu-id="447cf-116">`PATCH` Geriye dönük uyumlu hata düzeltmeleri yaptığınızda artırılır</span><span class="sxs-lookup"><span data-stu-id="447cf-116">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="447cf-117">Sürüm bilgileri .NET Kitaplığı'na uygularken yayın öncesi sürümleri vb. gibi diğer senaryoları belirtmek için yol vardır.</span><span class="sxs-lookup"><span data-stu-id="447cf-117">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="447cf-118">Geriye dönük uyumluluk</span><span class="sxs-lookup"><span data-stu-id="447cf-118">Backwards Compatibility</span></span>

<span data-ttu-id="447cf-119">Kitaplığınızın yeni sürümlerini yayınlama, geriye doğru önceki sürümlerle uyumluluk büyük olasılıkla önemli kaygılarınızdan olacaktır.</span><span class="sxs-lookup"><span data-stu-id="447cf-119">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="447cf-120">Yeni bir sürüm kitaplığınızın yeni sürümle yeniden derlenen, önceki sürümünde bağlı olan kod işe önceki bir sürümü ile uyumlu kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="447cf-120">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span> <span data-ttu-id="447cf-121">Kitaplığınızı yeni bir sürümü eski bir sürümüne bağımlı olan bir uygulama yeniden derleme, yeni sürümle birlikte çalışabilir ikili uyumlu ise.</span><span class="sxs-lookup"><span data-stu-id="447cf-121">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="447cf-122">Geriye dönük kitaplığınızın önceki sürümlerle uyumluluk sağlamak çalışırken dikkat etmeniz gerekenler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="447cf-122">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

* <span data-ttu-id="447cf-123">Sanal yöntemler: yaptığınızda sanal bir yöntem, yeni sürümde bu yöntemi yok sayın projeleri güncelleştirilmesi gerektiği anlamına gelir sanal olmayan.</span><span class="sxs-lookup"><span data-stu-id="447cf-123">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="447cf-124">Bu büyük bir değişiklik olup kesinlikle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="447cf-124">This is a huge breaking change and is strongly discouraged.</span></span>
* <span data-ttu-id="447cf-125">Yöntem imzaları: yöntemi davranışı güncelleştirme imzası de değiştirmenizi gerektirir, böylece bu yönteme çağırma kod çalışmaya devam eder, bunun yerine bir aşırı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="447cf-125">Method signatures: When updating a method behaviour requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="447cf-126">Her zaman uygulama tutarlı kalması yeni yöntem imzasının çağırmak için eski yöntem imzası clı'yle de işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="447cf-126">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
* <span data-ttu-id="447cf-127">[Geçersiz öznitelik](programming-guide/concepts/attributes/common-attributes.md#Obsolete): sınıflar veya kullanım dışı bırakılmıştır sınıf üyeleri belirlemek için kodunuzda bu özniteliği kullanabilirsiniz ve olması olası gelecek sürümleri kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="447cf-127">[Obsolete attribute](programming-guide/concepts/attributes/common-attributes.md#Obsolete): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span>
<span data-ttu-id="447cf-128">Bu, kitaplığı kullanan geliştiriciler önemli değişiklikler için daha iyi hazırlıklı olmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="447cf-128">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
* <span data-ttu-id="447cf-129">Yöntem bağımsız değişkenleri isteğe bağlı: Ne zaman daha önce isteğe bağlı bir yöntem bağımsız değişkenleri zorunlu yapmak veya varsayılan değerlerine sonra bu bağımsız değişken sağlamıyor tüm kod değiştirme güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="447cf-129">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>
> [!NOTE]
> <span data-ttu-id="447cf-130">Özellikle yöntemin davranışı değişmez gerekiyorsa zorunlu bağımsız değişkenler isteğe bağlı yapmak çok az etkisi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="447cf-130">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behaviour.</span></span>

<span data-ttu-id="447cf-131">Kolay bir şekilde, kullanıcılarınızın erken yükseltecek yeni sürüme kitaplığınızın, daha büyük olasılıkla yükseltme yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="447cf-131">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="447cf-132">Uygulama yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="447cf-132">Application Configuration File</span></span>

<span data-ttu-id="447cf-133">Çok yüksek kaybedilebilir önce karşılaştığınız bir .NET geliştiricisi olarak [ `app.config` dosya](../framework/configure-apps/file-schema/index.md) çoğu proje türlerinde mevcut.</span><span class="sxs-lookup"><span data-stu-id="447cf-133">As a .NET developer there's a very high chance you've encountered [the `app.config` file](../framework/configure-apps/file-schema/index.md) present in most project types.</span></span>
<span data-ttu-id="447cf-134">Bu basit bir yapılandırma dosyası, yeni güncelleştirme dağıtımı geliştirme içine uzun yol gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="447cf-134">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="447cf-135">Genellikle Kitaplıklarınızı düzenli olarak değiştirmek büyük olasılıkla bilgiler depolanır şekilde tasarlamanız gerekir, `app.config` , böylece tür bilgileri güncelleştirilirken dosya eski sürümlerinin yapılandırma dosyası yalnızca yeni bir tane ile değiştirilmesi gerekiyor Kitaplığı yeniden derleniyor gerek olmadan.</span><span class="sxs-lookup"><span data-stu-id="447cf-135">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="447cf-136">Kitaplıkları kullanma</span><span class="sxs-lookup"><span data-stu-id="447cf-136">Consuming Libraries</span></span>

<span data-ttu-id="447cf-137">Diğer geliştiriciler tarafından oluşturulan .NET kitaplıklarını tüketen bir geliştirici olarak büyük olasılıkla farkında kitaplığa yeni bir sürümü projenizle tam olarak uyumlu olmayabilir ve çoğunlukla kendinizi bu değişikliklerle çalışması için kodunuzu güncelleştirin gerek kalmadan bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="447cf-137">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="447cf-138">Şans sizin için C# ve .NET ekosisteminin gelir özellikleri ve uygulamamızı bozucu değişiklik yapabilecek kitaplıklarının yeni sürümleri ile çalışmak için kolayca güncelleştirmek bize izin teknikleri.</span><span class="sxs-lookup"><span data-stu-id="447cf-138">Lucky for you C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="447cf-139">Derleme bağlama yeniden yönlendirmesi</span><span class="sxs-lookup"><span data-stu-id="447cf-139">Assembly Binding Redirection</span></span>

<span data-ttu-id="447cf-140">Kullanabileceğiniz `app.config` dosya bir kitaplığı sürümünü güncelleştirmek için uygulama kullanır.</span><span class="sxs-lookup"><span data-stu-id="447cf-140">You can use the `app.config` file to update the version of a library your app uses.</span></span> <span data-ttu-id="447cf-141">Ne çağrılır ekleyerek bir [ *bağlama yeniden yönlendirmesi* ](../framework/configure-apps/redirect-assembly-versions.md) , uygulamanızı yeniden derlemenize gerek kalmadan yeni kitaplığı sürümünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="447cf-141">By adding what is called a [*binding redirect*](../framework/configure-apps/redirect-assembly-versions.md) your can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="447cf-142">Aşağıdaki örnek, uygulamanızın nasıl güncelleştiririz gösterir `app.config` kullanılacak dosyasını `1.0.1` düzeltme eki sürümü `ReferencedLibrary` yerine `1.0.0` , başlangıçta derlendiği sürümü.</span><span class="sxs-lookup"><span data-stu-id="447cf-142">The following example shows how you would update your app's `app.config` file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="447cf-143">Bu yaklaşım, yalnızca iş yeni sürümünü `ReferencedLibrary` uygulamanız ile ikili uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="447cf-143">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="447cf-144">Bkz: [geriye dönük uyumluluk](#backwards-compatibility) değişikliklerin için uyumluluk belirlerken dikkat için bölüm yukarıda.</span><span class="sxs-lookup"><span data-stu-id="447cf-144">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="447cf-145">new</span><span class="sxs-lookup"><span data-stu-id="447cf-145">new</span></span>

<span data-ttu-id="447cf-146">Kullandığınız `new` değiştiricisi devralınan bir temel sınıf üyelerinin gizlemek için.</span><span class="sxs-lookup"><span data-stu-id="447cf-146">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="447cf-147">Bu şekilde türetilmiş sınıflar temel sınıflar güncelleştirmeleri yanıt verebilir biridir.</span><span class="sxs-lookup"><span data-stu-id="447cf-147">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="447cf-148">Aşağıdaki örnek uygulayın:</span><span class="sxs-lookup"><span data-stu-id="447cf-148">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="447cf-149">**Output**</span><span class="sxs-lookup"><span data-stu-id="447cf-149">**Output**</span></span>

```
A base method
A derived method
```

<span data-ttu-id="447cf-150">Yukarıdaki örnekte gördüğünüz nasıl `DerivedClass` gizler `MyMethod` yöntemi mevcut `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="447cf-150">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="447cf-151">Bu bir temel sınıf kitaplığı'nın yeni sürümünde, türetilen bir sınıfta zaten bir üye eklediğinde, yalnızca kullanabileceğiniz anlamına gelir `new` temel sınıf üyeyi gizlemek için türetilmiş sınıf üye değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="447cf-151">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="447cf-152">Hiçbir `new` değiştiricisi belirtilirse, türetilmiş bir sınıf taban sınıfında çakışan üyeleri varsayılan olarak gizler, bir derleyici uyarısı oluşturulur ancak yine de kod derlenir.</span><span class="sxs-lookup"><span data-stu-id="447cf-152">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="447cf-153">Bu yalnızca yeni üyeler için varolan bir sınıf eklemek bu yeni sürüme kitaplığınızın aklınızdan anlamına gelir. hem kaynak hem de bağımlı kod ile uyumlu ikili.</span><span class="sxs-lookup"><span data-stu-id="447cf-153">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="447cf-154">override</span><span class="sxs-lookup"><span data-stu-id="447cf-154">override</span></span>

<span data-ttu-id="447cf-155">`override` Değiştiricisi türetilen uygulamaya bir temel sınıf üyesinin uygulamayı yaygınlaştırır yerine onu gizliyor anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="447cf-155">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="447cf-156">Temel sınıf üyesi olması gerekiyorsa `virtual` uygulanmış değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="447cf-156">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="447cf-157">**Output**</span><span class="sxs-lookup"><span data-stu-id="447cf-157">**Output**</span></span>

```
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="447cf-158">`override` Değiştiricisi, derleme zamanında değerlendirilir ve geçersiz kılmak için bir sanal üye bulamazsa, derleyici bir hata atar.</span><span class="sxs-lookup"><span data-stu-id="447cf-158">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="447cf-159">Bir kitaplık sürümleri arasında geçişin bir kolayca artırma konusunda uzun bir yol ele alındığı teknik bilginizi yanı sıra bunları kullanmak için hangi durumlarda Anlayışınızı geçer.</span><span class="sxs-lookup"><span data-stu-id="447cf-159">Your knowledge of the discussed techniques as well as your understanding of what situations to use them will go a long way to boost the ease of transition between versions of a library.</span></span>
