---
title: İstemci tarafı doğrulama (sunu katmanlarında doğrulama)
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | İstemci tarafı doğrulama (sunu katmanlarında doğrulama)
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 273aa0a8ceb7f683999f1074faae0a6aa303f9be
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="b5921-104">İstemci tarafı doğrulama (sunu katmanlarında doğrulama)</span><span class="sxs-lookup"><span data-stu-id="b5921-104">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="b5921-105">Gerçekte kaynak etki alanı modeldir ve sonuç olarak etki alanı model düzeyinde doğrulama olmalıdır bile hem etki alanı model düzeyinde (sunucu tarafı) hem de istemci tarafında doğrulama hala işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b5921-105">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the client side.</span></span>

<span data-ttu-id="b5921-106">İstemci tarafı doğrulama kullanıcıların harika bir kolaylık sağlamaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="b5921-106">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="b5921-107">Gidiş dönüş bekleniyor aksi harcadığınız zamanı doğrulama hataları döndürebilir sunucuya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b5921-107">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="b5921-108">İş açısından, saniyede yüzlerce kez her gün çarpılan bile birkaç kesirlerini ekler miktarda zaman, gider ve aksiliklerin.</span><span class="sxs-lookup"><span data-stu-id="b5921-108">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="b5921-109">Basit ve hemen doğrulama daha verimli olarak çalışabilir ve giriş ve çıkış daha iyi kalite üretmek kullanıcıların sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5921-109">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="b5921-110">Yalnızca görünüm modeli ve etki alanı modeli farklı olduğundan, görünüm model doğrulama ve etki alanı model doğrulama benzer ancak farklı bir amaca hizmet eder.</span><span class="sxs-lookup"><span data-stu-id="b5921-110">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="b5921-111">Endişe ediyorsanız bu durumda kodu yeniden kullanma bağlantı da gelebilir ve kurumsal uygulamalarda sunucu tarafı KURU ilkesini izleyin üzere daha istemci tarafı için eşleştiği değil daha da önemlisi KURU (yok yineleyin kendiniz İlkesi) hakkında göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="b5921-111">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="b5921-112">Bile istemci tarafı doğrulama kullanırken, her zaman komutlarınızı doğrulamak veya gerekir sunucunun API'leri olası bir saldırı vektörü olduğundan sunucu kodunda DTOs giriş.</span><span class="sxs-lookup"><span data-stu-id="b5921-112">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="b5921-113">Genellikle, her ikisini de yapmak UX açısından, bir istemci uygulaması varsa öngörülü ve geçersiz bilgi girmek için kullanıcıya izin verme en iyi olduğu için en iyi sonucu olur.</span><span class="sxs-lookup"><span data-stu-id="b5921-113">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="b5921-114">Bu nedenle, istemci-tarafı kodu, genellikle ViewModels doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="b5921-114">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="b5921-115">İstemci doğrulama hizmetlere göndermeden önce DTOs veya komutları çıktı.</span><span class="sxs-lookup"><span data-stu-id="b5921-115">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="b5921-116">İstemci tarafı doğrulama uyarlamasını ne tür bir istemci uygulaması oluşturmakta olduğunuz bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5921-116">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="b5921-117">.NET, JavaScript veya TypeScript, kodlanmış bu doğrulama SPA web uygulamasıyla kodda çoğunu MVC web uygulaması Web verilerle doğrulama gerekirse farklı olacak veya mobil uygulama, Xamarin ve C ile kodlanmış\#.</span><span class="sxs-lookup"><span data-stu-id="b5921-117">It will be different if you are validating data in a web MVC web application with most of the code in .NET, an SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C\#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b5921-118">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b5921-118">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="b5921-119">Xamarin mobil uygulamalarda doğrulama</span><span class="sxs-lookup"><span data-stu-id="b5921-119">Validation in Xamarin mobile apps</span></span>

-   <span data-ttu-id="b5921-120">**Metin giriş ve hataları göster doğrulamak**
    [*https://developer.xamarin.com/recipes/ios/standard\_denetimleri/metin\_alan ve doğrulama\_giriş /*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span><span class="sxs-lookup"><span data-stu-id="b5921-120">**Validate Text Input and Show Errors**
[*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span></span>

-   <span data-ttu-id="b5921-121">**Doğrulama geri çağırma**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span><span class="sxs-lookup"><span data-stu-id="b5921-121">**Validation Callback**
[*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span></span>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="b5921-122">ASP.NET Core uygulamaları doğrulama</span><span class="sxs-lookup"><span data-stu-id="b5921-122">Validation in ASP.NET Core apps</span></span>

-   <span data-ttu-id="b5921-123">**Rick Anderson. Doğrulama ekleme**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="b5921-123">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="b5921-124">SPA doğrulama Web uygulamaları (Açısal 2, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="b5921-124">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

-   <span data-ttu-id="b5921-125">**Ado Kukic. Açısal 2 Form doğrulama** **
    **[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span><span class="sxs-lookup"><span data-stu-id="b5921-125">**Ado Kukic. Angular 2 Form Validation** **
**[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span></span>

-   <span data-ttu-id="b5921-126">**Form doğrulama**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span><span class="sxs-lookup"><span data-stu-id="b5921-126">**Form Validation**
[*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span></span>

-   <span data-ttu-id="b5921-127">**Doğrulama.**</span><span class="sxs-lookup"><span data-stu-id="b5921-127">**Validation.**</span></span> <span data-ttu-id="b5921-128">Kolay belgeleri.</span><span class="sxs-lookup"><span data-stu-id="b5921-128">Breeze documentation.</span></span>
    [*http://breeze.github.io/doc-js/validation.html*](http://breeze.github.io/doc-js/validation.html)

<span data-ttu-id="b5921-129">Özet olarak, doğrulama gelince en önemli kavramları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b5921-129">In summary, these are the most important concepts in regards to validation:</span></span>

-   <span data-ttu-id="b5921-130">Varlıklar ve toplamalar kendi tutarlılığı zorlamak ve gerekir "her zaman geçerli".</span><span class="sxs-lookup"><span data-stu-id="b5921-130">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="b5921-131">Birleşik kökleri aynı toplama içinde varlıkla tutarlılık sorumludur.</span><span class="sxs-lookup"><span data-stu-id="b5921-131">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

-   <span data-ttu-id="b5921-132">Bir varlık geçersiz bir durum girin olması gerektiğini düşünüyorsanız, farklı nesne modelini kullanarak göz önünde bulundurun — Örneğin, son etki alanı varlığı oluşturana kadar geçici DTO kullanma.</span><span class="sxs-lookup"><span data-stu-id="b5921-132">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

-   <span data-ttu-id="b5921-133">Bir toplama gibi birkaç ilişkili nesneleri oluşturmanız gerekir ve bunların tümünün oluşturulduktan sonra yalnızca geçerli olduğu, Fabrika düzeni kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="b5921-133">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

-   <span data-ttu-id="b5921-134">Bir altyapı Framework'te güçlü bir bağımlılık uygulamanız gerekir çünkü doğrulama çerçeveleri sunu katmanı veya uygulama/hizmet katmanı gibi belirli katmanlarında ancak genellikle etki alanı modeli katmanı, en iyi şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b5921-134">Validation frameworks are best used in specific layers, such as the presentation layer or the application/service layer, but usually not in the domain model layer, because you would need to take a strong dependency on an infrastructure framework.</span></span>

-   <span data-ttu-id="b5921-135">Uygulama proaktif olabileceği için istemci tarafı yedekli doğrulama sahip iyi durumlarda çoğunda istenir.</span><span class="sxs-lookup"><span data-stu-id="b5921-135">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="b5921-136">[Önceki] (etki alanı-model-katman-validations.md) [sonraki] (etki alanı-olayları-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="b5921-136">[Previous] (domain-model-layer-validations.md) [Next] (domain-events-design-implementation.md)</span></span>
