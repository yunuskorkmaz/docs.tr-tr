---
title: İstemci tarafı doğrulaması (sunum katmanlarında doğrulama)
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | İstemci tarafı doğrulamanın temel kavramlarını gezin.
ms.date: 10/08/2018
ms.openlocfilehash: 4e72dcafafc3144a75afe1fd23a4a779f5667459
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295997"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="eca5b-103">İstemci tarafı doğrulaması (sunum katmanlarında doğrulama)</span><span class="sxs-lookup"><span data-stu-id="eca5b-103">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="eca5b-104">Gerçeği kaynağı etki alanı modeli olduğu ve sonunda etki alanı model düzeyinde doğrulamanız gerektiğinde bile, doğrulama yine de etki alanı modeli düzeyinde (sunucu tarafında) ve Kullanıcı arabiriminde (istemci tarafında) işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="eca5b-104">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the UI (client side).</span></span>

<span data-ttu-id="eca5b-105">İstemci tarafı doğrulama, kullanıcılar için harika bir kolaylık.</span><span class="sxs-lookup"><span data-stu-id="eca5b-105">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="eca5b-106">Aksi takdirde, doğrulama hataları döndürebilecek sunucuya gidiş dönüş için bekleyen harcamaları zaman kazandırır.</span><span class="sxs-lookup"><span data-stu-id="eca5b-106">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="eca5b-107">İş koşullarında, birkaç saniyelik bir saniyede yüzlerce kez, her gün çok fazla zaman, harcama ve hapasyon ekler.</span><span class="sxs-lookup"><span data-stu-id="eca5b-107">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="eca5b-108">Basit ve anında doğrulama, kullanıcıların daha verimli bir şekilde çalışmasını sağlar ve daha iyi kalitede giriş ve çıktı üretebilir.</span><span class="sxs-lookup"><span data-stu-id="eca5b-108">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="eca5b-109">Görüntüleme modeli ve etki alanı modelinin farklı olduğu gibi, model doğrulamasını görüntüleyin ve etki alanı modeli doğrulaması da benzer olabilir, ancak farklı bir amaç sunabilir.</span><span class="sxs-lookup"><span data-stu-id="eca5b-109">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="eca5b-110">KURUTMA (Kendini Tekrarlama prensibi) konusunda endişeleriniz varsa, bu durumda kodu yeniden kullanım için de bir de bu şekilde, kurumsal uygulamalarda sunucu tarafında kuru prensibi takip etmekle aynı şekilde sunucu tarafında daha önemli olduğunu düşünün.</span><span class="sxs-lookup"><span data-stu-id="eca5b-110">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="eca5b-111">İstemci tarafı doğrulaması kullanılırken bile, sunucu API 'Leri olası bir saldırı vektörü olduğundan, komutlarınızı veya sunucu kodundaki DTOs girdisini her zaman doğrulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="eca5b-111">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="eca5b-112">Genellikle, bir UX perspektifinden bir istemci uygulamanız varsa, bu, en iyi uygulamadır ve kullanıcının geçersiz bilgiler girmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="eca5b-112">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="eca5b-113">Bu nedenle, istemci tarafı kodunda genellikle Viewmodellerini doğrularsınız.</span><span class="sxs-lookup"><span data-stu-id="eca5b-113">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="eca5b-114">Ayrıca, Hizmetleri hizmetlere göndermeden önce istemci çıktı DTOs veya komutlarını da doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eca5b-114">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="eca5b-115">İstemci tarafı doğrulama uygulaması, oluşturmakta olduğunuz istemci uygulaması türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="eca5b-115">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="eca5b-116">Bir Web MVC web uygulamasındaki verileri .NET 'teki kodun çoğuna, JavaScript veya TypeScript 'te kodlandığı bir SPA Web uygulamasına ya da Xamarin ve C#ile kodlanmış bir mobil uygulamaya doğruladıysanız bu, farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="eca5b-116">It will be different if you are validating data in a web MVC web application with most of the code in .NET, a SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="eca5b-117">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="eca5b-117">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="eca5b-118">Xamarin mobil uygulamalarında doğrulama</span><span class="sxs-lookup"><span data-stu-id="eca5b-118">Validation in Xamarin mobile apps</span></span>

- <span data-ttu-id="eca5b-119">**Metin girişi doğrulama ve hataları gösterme** </span><span class="sxs-lookup"><span data-stu-id="eca5b-119">**Validate Text Input and Show Errors** </span></span>\
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- <span data-ttu-id="eca5b-120">**Doğrulama geri çağırması** </span><span class="sxs-lookup"><span data-stu-id="eca5b-120">**Validation Callback** </span></span>\
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="eca5b-121">ASP.NET Core uygulamalarda doğrulama</span><span class="sxs-lookup"><span data-stu-id="eca5b-121">Validation in ASP.NET Core apps</span></span>

- <span data-ttu-id="eca5b-122">**Rick Anderson. Doğrulama ekleme** </span><span class="sxs-lookup"><span data-stu-id="eca5b-122">**Rick Anderson. Adding validation** </span></span>\
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="eca5b-123">SPA Web uygulamalarında doğrulama (angular 2, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="eca5b-123">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

- <span data-ttu-id="eca5b-124">**ADO KuKic. Angular 2 form doğrulaması** </span><span class="sxs-lookup"><span data-stu-id="eca5b-124">**Ado Kukic. Angular 2 Form Validation** </span></span>\
  <https://scotch.io/tutorials/angular-2-form-validation>

- <span data-ttu-id="eca5b-125">**Form doğrulaması** </span><span class="sxs-lookup"><span data-stu-id="eca5b-125">**Form Validation** </span></span>\
  <https://angular.io/guide/form-validation>

- <span data-ttu-id="eca5b-126">**Doğrulamasına.**</span><span class="sxs-lookup"><span data-stu-id="eca5b-126">**Validation.**</span></span> <span data-ttu-id="eca5b-127">Belgeleri yeniden Başlat.</span><span class="sxs-lookup"><span data-stu-id="eca5b-127">Breeze documentation.</span></span> \
  <https://breeze.github.io/doc-js/validation.html>

<span data-ttu-id="eca5b-128">Özet bölümünde, doğrulama için en önemli kavramlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="eca5b-128">In summary, these are the most important concepts in regards to validation:</span></span>

- <span data-ttu-id="eca5b-129">Varlıklar ve toplamalar kendi tutarlılığını zorunlu tutar ve "her zaman geçerli" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eca5b-129">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="eca5b-130">Toplam kökler, aynı toplama içindeki çok varlıklık tutarlılığından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="eca5b-130">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

- <span data-ttu-id="eca5b-131">Bir varlığın geçersiz bir durum girmesi gerektiğini düşünüyorsanız, farklı bir nesne modeli kullanmayı düşünün — Örneğin, son etki alanı varlığını oluşturana kadar geçici bir DTO kullanma.</span><span class="sxs-lookup"><span data-stu-id="eca5b-131">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

- <span data-ttu-id="eca5b-132">Toplama gibi çeşitli ilgili nesneler oluşturmanız gerekiyorsa ve bunlar yalnızca tümü oluşturulduktan sonra geçerliyse, fabrika modelini kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="eca5b-132">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

- <span data-ttu-id="eca5b-133">Çoğu durumda, istemci tarafında gereksiz doğrulama yapmak iyi bir uygulamadır çünkü uygulama öngörülü olabilir.</span><span class="sxs-lookup"><span data-stu-id="eca5b-133">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="eca5b-134">[Önceki](domain-model-layer-validations.md)İleri
>[](domain-events-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="eca5b-134">[Previous](domain-model-layer-validations.md)
[Next](domain-events-design-implementation.md)</span></span>
