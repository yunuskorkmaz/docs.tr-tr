---
title: İstemci tarafı doğrulaması (sunum katmanlarında doğrulama)
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | İstemci tarafı doğrulamanın temel kavramlarını keşfedin.
ms.date: 10/08/2018
ms.openlocfilehash: 44c1e9fa280b19fcee87d4d1cdfcaa2ab9462f27
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988707"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="1bb1e-103">İstemci tarafı doğrulaması (sunum katmanlarında doğrulama)</span><span class="sxs-lookup"><span data-stu-id="1bb1e-103">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="1bb1e-104">Gerçeğin kaynağı etki alanı modeli olsa ve sonuçta etki alanı modeli düzeyinde doğrulama olması gerekir, doğrulama hala etki alanı modeli düzeyinde (sunucu tarafı) ve UI (istemci tarafı) hem de işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-104">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the UI (client side).</span></span>

<span data-ttu-id="1bb1e-105">İstemci tarafı doğrulama kullanıcılar için büyük bir kolaylıktır.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-105">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="1bb1e-106">Aksi takdirde doğrulama hataları döndürebilir sunucuya bir gidiş dönüş için bekleyen harcamak zaman kazandırır.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-106">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="1bb1e-107">İş açısından, saniyebile birkaç kesirleri her gün yüzlerce kez çarpılır zaman, gider ve hayal kırıklığı bir sürü ekler.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-107">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="1bb1e-108">Basit ve anında doğrulama, kullanıcıların daha verimli çalışmasını ve daha kaliteli giriş ve çıktı üretmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-108">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="1bb1e-109">Görünüm modeli ve etki alanı modeli farklı olduğu gibi, görünüm modeli doğrulama ve etki alanı modeli doğrulama benzer olabilir ama farklı bir amaca hizmet.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-109">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="1bb1e-110">DRY (Kendini TekrarEtme ilkesi) konusunda endişeleriniz varsa, bu durumda kodun yeniden kullanılmasının bağlantı anlamına gelebileceğini ve kurumsal uygulamalarda sunucu tarafını istemci tarafına çiftle etmemenin DRY ilkesine uymaktan daha önemli olduğunu düşünün.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-110">If you are concerned about DRY (the Don't Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="1bb1e-111">İstemci tarafı doğrulamayı kullanırken bile, sunucu API'leri olası bir saldırı vektörü olduğundan, komutlarınızı her zaman doğrulamanız veya sunucu kodundaki DTO'lar girin.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-111">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="1bb1e-112">Genellikle, her ikisini de yapmak en iyi bahistir, çünkü ux perspektifinden bir istemci uygulamanız varsa, proaktif olmak ve kullanıcının geçersiz bilgileri girmesine izin vermemek en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-112">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="1bb1e-113">Bu nedenle, istemci tarafı kodunda genellikle Görünüm Modelleri doğrular.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-113">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="1bb1e-114">Ayrıca, istemci çıktı DTOs veya komutları hizmetlere göndermeden önce doğrulayabilir.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-114">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="1bb1e-115">İstemci tarafı doğrulamanın uygulanması, ne tür istemci uygulaması oluşturmakta olduğunuza bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-115">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="1bb1e-116">Bir web MVC web uygulamasındaki verileri .NET'teki kodun çoğuyla, JavaScript veya TypeScript'te kodlanmış bir SPA web uygulamasına veya Xamarin ve C# kodlu bir mobil uygulamayla doğruluyorsanız, bu farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-116">It will be different if you are validating data in a web MVC web application with most of the code in .NET, a SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="1bb1e-117">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="1bb1e-117">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="1bb1e-118">Xamarin mobil uygulamalarında doğrulama</span><span class="sxs-lookup"><span data-stu-id="1bb1e-118">Validation in Xamarin mobile apps</span></span>

- <span data-ttu-id="1bb1e-119">**Metin Girişini Doğrula ve Hataları Göster** </span><span class="sxs-lookup"><span data-stu-id="1bb1e-119">**Validate Text Input and Show Errors** </span></span>\
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- <span data-ttu-id="1bb1e-120">**Doğrulama Geri Arama** </span><span class="sxs-lookup"><span data-stu-id="1bb1e-120">**Validation Callback** </span></span>\
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="1bb1e-121">ASP.NET Core uygulamalarında doğrulama</span><span class="sxs-lookup"><span data-stu-id="1bb1e-121">Validation in ASP.NET Core apps</span></span>

- <span data-ttu-id="1bb1e-122">**Rick Anderson' ı. Doğrulama ekleme** </span><span class="sxs-lookup"><span data-stu-id="1bb1e-122">**Rick Anderson. Adding validation** </span></span>\
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="1bb1e-123">SPA Web uygulamalarında doğrulama (Açısal 2, TypeScript, JavaScript)</span><span class="sxs-lookup"><span data-stu-id="1bb1e-123">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

- <span data-ttu-id="1bb1e-124">**Ado Kukiç. Açısal 2 Form Doğrulama** </span><span class="sxs-lookup"><span data-stu-id="1bb1e-124">**Ado Kukic. Angular 2 Form Validation** </span></span>\
  <https://scotch.io/tutorials/angular-2-form-validation>

- <span data-ttu-id="1bb1e-125">**Form Doğrulama** </span><span class="sxs-lookup"><span data-stu-id="1bb1e-125">**Form Validation** </span></span>\
  <https://angular.io/guide/form-validation>

- <span data-ttu-id="1bb1e-126">**Doğrulama.**</span><span class="sxs-lookup"><span data-stu-id="1bb1e-126">**Validation.**</span></span> <span data-ttu-id="1bb1e-127">Meltem belgeleri.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-127">Breeze documentation.</span></span> \
  <https://breeze.github.io/doc-js/validation.html>

<span data-ttu-id="1bb1e-128">Özetle, doğrulama ile ilgili en önemli kavramlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1bb1e-128">In summary, these are the most important concepts in regards to validation:</span></span>

- <span data-ttu-id="1bb1e-129">Varlıklar ve agregalar kendi tutarlılıklarını uygulamalı ve "her zaman geçerli" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-129">Entities and aggregates should enforce their own consistency and be "always valid".</span></span> <span data-ttu-id="1bb1e-130">Toplam kökler, aynı toplam içinde çoklu varlık tutarlılığından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-130">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

- <span data-ttu-id="1bb1e-131">Bir varlığın geçersiz bir durum girmesi gerektiğini düşünüyorsanız, örneğin, son etki alanı varlığını oluşturana kadar geçici bir DTO kullanarak farklı bir nesne modeli kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-131">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

- <span data-ttu-id="1bb1e-132">Bir agrega gibi birkaç ilgili nesne oluşturmanız gerekiyorsa ve bunların yalnızca tümü oluşturulduktan sonra geçerliyse, Fabrika deseni kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-132">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

- <span data-ttu-id="1bb1e-133">Çoğu durumda, uygulama proaktif olabileceğinden, istemci tarafında gereksiz doğrulama olması iyidir.</span><span class="sxs-lookup"><span data-stu-id="1bb1e-133">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1bb1e-134">[Önceki](domain-model-layer-validations.md)
>[Sonraki](domain-events-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="1bb1e-134">[Previous](domain-model-layer-validations.md)
[Next](domain-events-design-implementation.md)</span></span>
