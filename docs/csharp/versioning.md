---
title: "C# sürüm oluşturma - C# Kılavuzu"
description: "C# ve .NET sürüm nasıl çalıştığını anlamak"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.date: 01/08/2017
ms.topic: article
ms.prod: visual-studio-dev-14
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 153e7d115b34e6659f6a8ca23014441b86847796
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="versioning-in-c"></a><span data-ttu-id="0d1d0-104">C# sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d1d0-104">Versioning in C#</span></span> #

<span data-ttu-id="0d1d0-105">Bu öğreticide, .NET içinde hangi sürüm oluşturma anlamına gelir öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-105">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="0d1d0-106">Dikkate almanız gereken faktörler bilgi edineceksiniz sürüm kitaplığınızın yanı sıra yeni bir sürümüne yükseltme kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-106">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of the a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="0d1d0-107">Geliştirme kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="0d1d0-107">Authoring Libraries</span></span>

<span data-ttu-id="0d1d0-108">.NET kitaplıklarına genel kullanım için oluşturan bir geliştirici olarak seçtiğiniz en yeni güncelleştirmeleri almak için sahip olduğu durumlarda büyük olasılıkla bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-108">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="0d1d0-109">Varolan kod kitaplığınızın yeni sürüme sorunsuz bir geçiş olduğundan emin olmak gereksinim duyduğunuz bu işlem hakkında nasıl gittiğiniz çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-109">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="0d1d0-110">Yeni bir sürüm oluştururken dikkate alınması gereken birkaç nokta şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0d1d0-110">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="0d1d0-111">Anlamsal sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d1d0-111">Semantic Versioning</span></span>

<span data-ttu-id="0d1d0-112">[Anlamsal sürüm oluşturma](http://semver.org/) (kısaca SemVer) olan belirli aşama olayları belirtmek için kitaplık sürümleri için uygulanan bir adlandırma kuralı.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-112">[Semantic versioning](http://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="0d1d0-113">İdeal olarak, kitaplığınızın size sürüm bilgilerini geliştiriciler, eski sürümleri aynı kullanan projelerini uyumluluğunu belirlemek yardımcı olmalıdır kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-113">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="0d1d0-114">SemVer en temel yaklaşım 3 bileşeni biçimidir `MAJOR.MINOR.PATCH`, burada:</span><span class="sxs-lookup"><span data-stu-id="0d1d0-114">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>
 
* <span data-ttu-id="0d1d0-115">`MAJOR`uyumsuz API değişiklikler yaptığınızda artırılır</span><span class="sxs-lookup"><span data-stu-id="0d1d0-115">`MAJOR` is incremented when you make incompatible API changes</span></span>
* <span data-ttu-id="0d1d0-116">`MINOR`Geriye dönük olarak uyumlu bir biçimde işlevselliği eklediğinizde artırılır</span><span class="sxs-lookup"><span data-stu-id="0d1d0-116">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
* <span data-ttu-id="0d1d0-117">`PATCH`Geriye dönük olarak uyumlu hata düzeltmeleri yaptığınızda artırılır</span><span class="sxs-lookup"><span data-stu-id="0d1d0-117">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="0d1d0-118">Sürüm bilgileri .NET Kitaplığı'na uygularken yayın öncesi sürümleri vb. gibi diğer senaryolar belirtmek için yolları da vardır.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-118">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="0d1d0-119">Geriye dönük uyumluluk</span><span class="sxs-lookup"><span data-stu-id="0d1d0-119">Backwards Compatibility</span></span>

<span data-ttu-id="0d1d0-120">Yeni sürümler kitaplığınızın yayım, geriye doğru önceki sürümleriyle uyumluluğunu büyük olasılıkla önemli kaygılarınızdan biri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-120">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="0d1d0-121">Yeni bir sürüm kitaplığınızın önceki sürüme bağlıdır kodu yeniden derlenmesi, yeni sürümle birlikte çalışabilir önceki bir sürümüyle uyumlu kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-121">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span> <span data-ttu-id="0d1d0-122">Yeni bir sürüm kitaplığınızın eski sürümüne bağımlı olduğu bir uygulamayı yeniden derlenmek yeni sürümü ile çalışabilir ikili uyumlu ise.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-122">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="0d1d0-123">Geriye dönük kitaplığınızın eski sürümleriyle uyumluluğunu korumak çalışırken göz önünde bulundurmanız gereken bazı şeyler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0d1d0-123">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

* <span data-ttu-id="0d1d0-124">Sanal yöntemler: yaptığınızda sanal bir yöntem sürümünüzde anlamına gelir bu yöntemi yok sayın projeleri güncelleştirilmesi gerekecek yeni sanal olmayan.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-124">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="0d1d0-125">Bu büyük önemli bir değişiklik ve kesinlikle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-125">This is a huge breaking change and is strongly discouraged.</span></span>
* <span data-ttu-id="0d1d0-126">Yöntem imzaları: yöntemi davranışa güncelleştirme imzası da değiştirmenizi gerektirdiğinde, böylece bu yönteme çağırma kodu çalışmaya devam eder, bunun yerine bir aşırı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-126">Method signatures: When updating a method behaviour requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="0d1d0-127">Uygulama tutarlı kalmayacak şekilde yeni yöntemi imzaya çağırmak için eski yöntemi imza her zaman yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-127">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
* <span data-ttu-id="0d1d0-128">[Geçersiz öznitelik](programming-guide/concepts/attributes/common-attributes.md#Obsolete): sınıfları veya kullanım dışı bırakılmıştır sınıf üyeleri belirtmek için bu öznitelik, kodunuzda kullanabilirsiniz ve olması olası gelecek sürümlerinde kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-128">[Obsolete attribute](programming-guide/concepts/attributes/common-attributes.md#Obsolete): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span>
<span data-ttu-id="0d1d0-129">Bu kitaplık kullanan geliştiriciler, daha iyi önemli değişiklikler için hazırlanır sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-129">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
* <span data-ttu-id="0d1d0-130">İsteğe bağlı yöntemi bağımsız değişkenler: Güncelleştirilmesi zaman daha önce isteğe bağlı yöntem bağımsız değişkenleri zorunlu yapmanız veya varsayılan değerlerine sonra bu bağımsız değişkenlerden sağlamıyor tüm kodu değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-130">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>
> [!NOTE]
> <span data-ttu-id="0d1d0-131">Özellikle yöntemin davranışları değiştirmez gerekiyorsa zorunlu bağımsız değişkenler isteğe bağlı yapmak çok az etkisi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-131">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behaviour.</span></span>

<span data-ttu-id="0d1d0-132">Daha kolay, erken yükseltecek yeni kitaplığınızın, büyük olasılıkla'sürümüne yükseltmek, kullanıcılarınızın olun.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-132">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="0d1d0-133">Uygulama yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="0d1d0-133">Application Configuration File</span></span>

<span data-ttu-id="0d1d0-134">Çok yüksek olasılığı yüksektir karşılaştı .NET geliştiricisi olarak [ `app.config` dosya](https://msdn.microsoft.com/library/1fk1t1t0(v=vs.110).aspx) çoğu proje türleri de mevcut.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-134">As a .NET developer there's a very high chance you've encountered [the `app.config` file](https://msdn.microsoft.com/library/1fk1t1t0(v=vs.110).aspx) present in most project types.</span></span>
<span data-ttu-id="0d1d0-135">Bu basit yapılandırma dosyası depoladıysanız yeni güncelleştirmeler sunum geliştirme içine gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-135">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="0d1d0-136">Genellikle Kitaplıklarınızı düzenli olarak değiştirmek büyük olasılıkla bilgiler saklanır şekilde tasarlamanız gerekir, `app.config` , böylece gibi bilgileri güncelleştirildiğinde dosya eski sürümlerinin yapılandırma dosyası yalnızca yeni bir bağlantıyla değiştirilmesi gerekiyor Kitaplığı yeniden derlenmek gerek olmadan.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-136">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="0d1d0-137">Kitaplıkları kullanma</span><span class="sxs-lookup"><span data-stu-id="0d1d0-137">Consuming Libraries</span></span>

<span data-ttu-id="0d1d0-138">.NET kitaplıklarına diğer geliştiriciler tarafından oluşturulmuş tüketen geliştirici olarak kitaplığa yeni bir sürümü projenizi ile tamamen uyumlu olmayabilir ve genellikle kendinizi kodunuzu bu değişikliklerle çalışması için update gerek kalmadan bulabilirsiniz büyük olasılıkla aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-138">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="0d1d0-139">Sizin için şanslı C# ve .NET ekosistemi ile birlikte gelen özellikleri ve bize uygulamamıza önemli değişiklikler yapabilecek kitaplıkları yeni sürümleri ile çalışmak için kolayca güncelleştirmeye izin teknikler.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-139">Lucky for you C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="0d1d0-140">Derleme bağlaması yeniden yönlendirme</span><span class="sxs-lookup"><span data-stu-id="0d1d0-140">Assembly Binding Redirection</span></span>

<span data-ttu-id="0d1d0-141">Kullanabileceğiniz `app.config` dosya bir kitaplık sürümünü güncelleştirmek için uygulama kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-141">You can use the `app.config` file to update the version of a library your app uses.</span></span> <span data-ttu-id="0d1d0-142">Ne adlı ekleyerek bir [ *bağlama yeniden yönlendirmesinin* ](https://msdn.microsoft.com/library/7wd6ex19(v=vs.110).aspx) , yeni kitaplık sürümü, uygulamanızın yeniden derlemenize gerek kalmadan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-142">By adding what is called a [*binding redirect*](https://msdn.microsoft.com/library/7wd6ex19(v=vs.110).aspx) your can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="0d1d0-143">Aşağıdaki örnek, uygulamanızın nasıl güncelleştirecektir gösterir `app.config` kullanmak üzere bir dosya `1.0.1` düzeltme eki sürümü `ReferencedLibrary` yerine `1.0.0` , ilk olarak derlenmiş ile sürümü.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-143">The following example shows how you would update your app's `app.config` file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="0d1d0-144">Bu yaklaşım, yalnızca işe yeni sürümünü `ReferencedLibrary` uygulamanız ile ikili uyumlu.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-144">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="0d1d0-145">Bkz: [geriye dönük uyumluluk](#backwards-compatibility) değişikliklerin uyumluluk belirlerken arayın için bölüm üstünde.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-145">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="0d1d0-146">new</span><span class="sxs-lookup"><span data-stu-id="0d1d0-146">new</span></span>

<span data-ttu-id="0d1d0-147">Kullandığınız `new` devralınan bir taban sınıfı üyeleri gizlemek için değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-147">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="0d1d0-148">Bu şekilde türetilmiş sınıflar temel sınıflar güncelleştirmelerinde yanıt vermesini sağlayabilirsiniz biridir.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-148">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="0d1d0-149">Aşağıdaki örnek alın:</span><span class="sxs-lookup"><span data-stu-id="0d1d0-149">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="0d1d0-150">**Output**</span><span class="sxs-lookup"><span data-stu-id="0d1d0-150">**Output**</span></span>

```
A base method
A derived method
```

<span data-ttu-id="0d1d0-151">Yukarıdaki örnekte gördüğünüz nasıl `DerivedClass` gizler `MyMethod` yöntemi mevcut `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-151">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="0d1d0-152">Bu bir taban sınıf kitaplığı'nın yeni sürümünde türetilen sınıfta zaten bir üye eklediğinde, yalnızca kullanabileceğiniz anlamına gelir `new` temel sınıf üyesi gizlemek için türetilmiş sınıf üyesi değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-152">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="0d1d0-153">Durumlarda `new` değiştiricisi belirtilirse, türetilmiş bir sınıf bir taban sınıf çakışan üyelerinde varsayılan olarak gizlenir, kod derleyici uyarısı oluşturulur ancak hala derlenir.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-153">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="0d1d0-154">Bu yalnızca varolan bir sınıfa yeni üye ekleme kitaplığınızın yeni sürümünün yapar anlamına gelir hem kaynak hem de ikili bağımlı kod ile uyumlu.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-154">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="0d1d0-155">override</span><span class="sxs-lookup"><span data-stu-id="0d1d0-155">override</span></span>

<span data-ttu-id="0d1d0-156">`override` Türetilmiş uygulamasına bir temel sınıf üyesi uyarlamasını genişletir yerine gizler değiştiricisi anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-156">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="0d1d0-157">Taban sınıf üyesi olması gerekiyorsa `virtual` uygulanan değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-157">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="0d1d0-158">**Output**</span><span class="sxs-lookup"><span data-stu-id="0d1d0-158">**Output**</span></span>

```
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="0d1d0-159">`override` Değiştiricisi derleme zamanında değerlendirilir ve geçersiz kılmak için sanal üyesi bulamazsa derleyici bir hata özel durum oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-159">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="0d1d0-160">Bir kitaplık sürümleri arasında geçiş kolaylığı artırmak için uzun bir yol bilginiz ele teknikleri ve aynı zamanda bunları kullanmak için hangi durumlarda Anlayışınızı geçer.</span><span class="sxs-lookup"><span data-stu-id="0d1d0-160">Your knowledge of the discussed techniques as well as your understanding of what situations to use them will go a long way to boost the ease of transition between versions of a library.</span></span>
