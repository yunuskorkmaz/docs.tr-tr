---
title: İstemci tarafı doğrulaması (sunum katmanlarında doğrulama)
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | İstemci tarafı doğrulama temel kavramlarını keşfedin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 4c039356e94f843c75430ff61d5fe68906c5c0ed
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633835"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="7e687-103">İstemci tarafı doğrulaması (sunum katmanlarında doğrulama)</span><span class="sxs-lookup"><span data-stu-id="7e687-103">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="7e687-104">Etki alanı modeli gerçekte kaynağıdır ve sonuç olarak etki alanı model düzeyinde doğrulama olmalıdır bile hem etki alanı model düzeyi (sunucu tarafı) hem de kullanıcı Arabirimi (istemci tarafı) doğrulama hala işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="7e687-104">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the UI (client side).</span></span>

<span data-ttu-id="7e687-105">İstemci tarafı doğrulama, kullanıcılar için harika bir kolaylığıdır.</span><span class="sxs-lookup"><span data-stu-id="7e687-105">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="7e687-106">Gidiş dönüş bekleniyor aksi açabiliyorduk zaman doğrulama hataları döndürebilir sunucuya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="7e687-106">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="7e687-107">İş dünyasında bile birkaç kez her gün yüzlerce çarpılan saniyelerin kesirlerini ekler miktarda zaman harcama ve sıkıntıya.</span><span class="sxs-lookup"><span data-stu-id="7e687-107">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="7e687-108">Basit ve anında doğrulama kullanıcıların giriş ve çıkış daha iyi kalite üreten ve daha verimli çalışmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7e687-108">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="7e687-109">Yalnızca görünüm modeli ve etki alanı modeli farklı olduğundan, görünüm model doğrulama ve etki alanı model doğrulama benzer ancak farklı bir amaca hizmet.</span><span class="sxs-lookup"><span data-stu-id="7e687-109">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="7e687-110">İlgili ise bu durumda kod yeniden kullanımını bağlantısından de gelebilir ve kurumsal uygulamaları, sunucu tarafı KURU ilkesini izleyin üzere daha istemci tarafı için eşleştiği değil daha önemlidir (yoksa yineleyin kendiniz İlkesi) KURU hakkında göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7e687-110">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="7e687-111">Bile istemci tarafında doğrulama kullanırken her zaman komutlarınızı doğruladığınızda veya sunucu API'leri olası bir saldırı vektörü olduğundan sunucu kodunda Dto'lar giriş.</span><span class="sxs-lookup"><span data-stu-id="7e687-111">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="7e687-112">Genellikle, ikisini de uygulamak UX açısından, bir istemci uygulaması varsa, proaktif ve geçersiz bilgi girmek için kullanıcıya izin en iyi olduğundan, en iyi sonuç olur.</span><span class="sxs-lookup"><span data-stu-id="7e687-112">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="7e687-113">Bu nedenle, istemci tarafı kod, genellikle Viewmodel'lar doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="7e687-113">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="7e687-114">Ayrıca istemci doğrulama hizmetlere göndermeden önce Dto'lar veya komutları çıktı.</span><span class="sxs-lookup"><span data-stu-id="7e687-114">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="7e687-115">İstemci tarafı doğrulama uygulanması, oluşturduğunuz ne tür bir istemci uygulaması bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7e687-115">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="7e687-116">Xamarin ile mobil uygulama kodlanmış veya .NET, JavaScript veya TypeScript, kodlanmış bu doğrulama SPA web uygulamasıyla kodda çoğunu bir MVC web uygulaması Web verilerle doğrulamakta olduğunuz, farklı olacaktır ve C#.</span><span class="sxs-lookup"><span data-stu-id="7e687-116">It will be different if you are validating data in a web MVC web application with most of the code in .NET, a SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7e687-117">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7e687-117">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="7e687-118">Xamarin mobil uygulamalarında doğrulama</span><span class="sxs-lookup"><span data-stu-id="7e687-118">Validation in Xamarin mobile apps</span></span>

- <span data-ttu-id="7e687-119">**Metin doğrulamak giriş ve hatalarını gösterme** \\</span><span class="sxs-lookup"><span data-stu-id="7e687-119">**Validate Text Input and Show Errors** \\</span></span>
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- <span data-ttu-id="7e687-120">**Doğrulama geri çağırma** \\</span><span class="sxs-lookup"><span data-stu-id="7e687-120">**Validation Callback** \\</span></span>
  [https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="7e687-121">ASP.NET Core uygulamaları doğrulama</span><span class="sxs-lookup"><span data-stu-id="7e687-121">Validation in ASP.NET Core apps</span></span>

- <span data-ttu-id="7e687-122">**Rick Anderson. Doğrulama ekleme** \\</span><span class="sxs-lookup"><span data-stu-id="7e687-122">**Rick Anderson. Adding validation** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="7e687-123">SPA doğrulama Web uygulamaları (Angular 2, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="7e687-123">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

- <span data-ttu-id="7e687-124">**Ado Kukic. Angular 2 Form doğrulama** \\</span><span class="sxs-lookup"><span data-stu-id="7e687-124">**Ado Kukic. Angular 2 Form Validation** \\</span></span>
  [https://scotch.io/tutorials/angular-2-form-validation](https://scotch.io/tutorials/angular-2-form-validation)

- <span data-ttu-id="7e687-125">**Form doğrulaması** \\</span><span class="sxs-lookup"><span data-stu-id="7e687-125">**Form Validation** \\</span></span>
  [https://angular.io/docs/ts/latest/cookbook/form-validation.html](https://angular.io/docs/ts/latest/cookbook/form-validation.html)

- <span data-ttu-id="7e687-126">**Doğrulama.**</span><span class="sxs-lookup"><span data-stu-id="7e687-126">**Validation.**</span></span> <span data-ttu-id="7e687-127">Meltem belgeleri.</span><span class="sxs-lookup"><span data-stu-id="7e687-127">Breeze documentation.</span></span> \
  [https://breeze.github.io/doc-js/validation.html](https://breeze.github.io/doc-js/validation.html)

<span data-ttu-id="7e687-128">Özet olarak, doğrulama ilgili en önemli kavramları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7e687-128">In summary, these are the most important concepts in regards to validation:</span></span>

- <span data-ttu-id="7e687-129">Varlıklar ve toplamalar kendi tutarlılığın ve "her zaman geçerli".</span><span class="sxs-lookup"><span data-stu-id="7e687-129">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="7e687-130">Toplama kökleri aynı toplama içinde birden çok varlık tutarlılığı sorumludur.</span><span class="sxs-lookup"><span data-stu-id="7e687-130">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

- <span data-ttu-id="7e687-131">Bir varlık geçersiz bir durumda girmeniz gerektiğini düşünüyorsanız, farklı nesne modelini kullanarak göz önünde bulundurun — Örneğin, son etki alanı varlığı oluşturana kadar geçici bir DTO'ni kullanarak.</span><span class="sxs-lookup"><span data-stu-id="7e687-131">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

- <span data-ttu-id="7e687-132">Bir toplama gibi birçok ilgili nesneleri oluşturmanız gerekir ve bunların tümünü oluşturulduktan sonra yalnızca geçerli olduğu Fabrika deseni kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="7e687-132">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

- <span data-ttu-id="7e687-133">Uygulama proaktif olarak olabileceğinden çalışmalarının çoğu istemci tarafı yedekli doğrulama sahip, uygundur.</span><span class="sxs-lookup"><span data-stu-id="7e687-133">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7e687-134">[Önceki](domain-model-layer-validations.md)
>[İleri](domain-events-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="7e687-134">[Previous](domain-model-layer-validations.md)
[Next](domain-events-design-implementation.md)</span></span>
