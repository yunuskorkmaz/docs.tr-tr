---
title: Açık kaynak .NET kitaplık Kılavuzu
description: Geliştiricilerin yüksek kaliteli .NET kitaplıkları oluşturmak en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/17/2018
ms.openlocfilehash: a656094066eb43ffe64ab405784f4577621b5c46
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910136"
---
# <a name="open-source-library-guidance"></a><span data-ttu-id="178be-103">Açık kaynak kitaplık kılavuzu</span><span class="sxs-lookup"><span data-stu-id="178be-103">Open-source library guidance</span></span>

<span data-ttu-id="178be-104">Bu kılavuz, geliştiricilerin yüksek kaliteli .NET kitaplıkları oluşturmak öneriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="178be-104">This guidance provides recommendations for developers to create high-quality .NET libraries.</span></span> <span data-ttu-id="178be-105">Bu belge odaklanır *ne* ve *neden* olmayan bir .NET kitaplığı oluşturma sırasında *nasıl*.</span><span class="sxs-lookup"><span data-stu-id="178be-105">This documentation focuses on the *what* and the *why* when building a .NET library, not the *how*.</span></span>

<span data-ttu-id="178be-106">Yüksek kaliteli açık kaynak .NET kitaplıkları yönlerini:</span><span class="sxs-lookup"><span data-stu-id="178be-106">Aspects of high-quality open-source .NET libraries:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="178be-107">**Kapsamlı** -iyi .NET kitaplıkları çaba birçok Platform, programlama dilleri ve uygulamaları desteklemek.</span><span class="sxs-lookup"><span data-stu-id="178be-107">**Inclusive** - Good .NET libraries strive to support many platforms, programming languages, and applications.</span></span>
> * <span data-ttu-id="178be-108">**Kararlı** -birçok kitaplıkları ile oluşturulan uygulamalar çalışan .NET ekosisteminde iyi .NET kitaplıkları bir arada.</span><span class="sxs-lookup"><span data-stu-id="178be-108">**Stable** - Good .NET libraries coexist in the .NET ecosystem, running in applications built with many libraries.</span></span>
> * <span data-ttu-id="178be-109">**Gelişmek için tasarlanmış** -.NET kitaplıkları artırmak ve zamandan, var olan kullanıcıları desteklemek için üzerinde evrim Geçiren.</span><span class="sxs-lookup"><span data-stu-id="178be-109">**Designed to evolve** - .NET libraries should improve and evolve over time, while supporting existing users.</span></span>
> * <span data-ttu-id="178be-110">**Hata ayıklanabilir** -.NET kitaplıkları, kullanıcılar için harika bir hata ayıklama deneyimi oluşturmak için en yeni araçlara kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="178be-110">**Debuggable** - .NET libraries should use the latest tools to create a great debugging experience for users.</span></span>
> * <span data-ttu-id="178be-111">**Güvenilen** -.NET kitaplıkları, NuGet kullanarak en iyi güvenlik uygulamaları yayımlayarak geliştiricilerin güven sahip.</span><span class="sxs-lookup"><span data-stu-id="178be-111">**Trusted** - .NET libraries have developers' trust by publishing to NuGet using security best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="178be-112">Başlarken</span><span class="sxs-lookup"><span data-stu-id="178be-112">Get Started</span></span>](./get-started.md)

## <a name="types-of-recommendations"></a><span data-ttu-id="178be-113">Öneri türü</span><span class="sxs-lookup"><span data-stu-id="178be-113">Types of recommendations</span></span>

<span data-ttu-id="178be-114">Her bir makaleyi dört tür önerileri sunar: **Yapmak**, **göz önünde bulundurun**, **önlemek**, ve **olmayan**.</span><span class="sxs-lookup"><span data-stu-id="178be-114">Each article presents four types of recommendations: **Do**, **Consider**, **Avoid**, and **Do not**.</span></span> <span data-ttu-id="178be-115">Ne kadar güçlü gelmelidir önerinin türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="178be-115">The type of recommendation indicates how strongly it should be followed.</span></span>

<span data-ttu-id="178be-116">Neredeyse her zaman izlemeniz gereken bir **yapmak** öneri.</span><span class="sxs-lookup"><span data-stu-id="178be-116">You should almost always follow a **Do** recommendation.</span></span> <span data-ttu-id="178be-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="178be-117">For example:</span></span>

<span data-ttu-id="178be-118">**✔️ YAPMAK** bir NuGet paketi kullanarak kitaplığınızda dağıtın.</span><span class="sxs-lookup"><span data-stu-id="178be-118">**✔️ DO** distribute your library using a NuGet package.</span></span>

<span data-ttu-id="178be-119">Öte yandan, **düşünün** önerileri genellikle sonrasında, ancak kuralın yasal özel durumu vardır ve yönergeleri izleyerek değil hatalı düşündüğünüz olmamalıdır:</span><span class="sxs-lookup"><span data-stu-id="178be-119">On the other hand, **Consider** recommendations should generally be followed, but there are legitimate exceptions to the rule and you shouldn't feel bad about not following the guidance:</span></span>

<span data-ttu-id="178be-120">**✔️ DÜŞÜNÜN** kullanarak [SemVer 2.0.0](https://semver.org/) sürümüne NuGet paketinizi.</span><span class="sxs-lookup"><span data-stu-id="178be-120">**✔️ CONSIDER** using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="178be-121">**Önlemek** önerileri bahsetmek genellikle iyi bir fikir olmayan bir şey, ancak bazen kural bozucu anlamlı:</span><span class="sxs-lookup"><span data-stu-id="178be-121">**Avoid** recommendations mention things that are generally not a good idea, but breaking the rule sometimes makes sense:</span></span>

<span data-ttu-id="178be-122">**❌ KAÇININ** tam bir sürümünü gerektirdiğinden NuGet paket başvuruları.</span><span class="sxs-lookup"><span data-stu-id="178be-122">**❌ AVOID** NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="178be-123">Son olarak, **olmayan** önerileri neredeyse hiç yapmanız bir şey gösterir:</span><span class="sxs-lookup"><span data-stu-id="178be-123">And finally, **Do not** recommendations indicate something you should almost never do:</span></span>

<span data-ttu-id="178be-124">**❌ SAĞLAMADIĞI** kitaplığınızın tanımlayıcı adlı ve olmayan-tanımlayıcı adlı sürümler yayımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="178be-124">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="178be-125">Örneğin, `Contoso.Api` ve `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="178be-125">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="178be-126">Next</span><span class="sxs-lookup"><span data-stu-id="178be-126">Next</span></span>](get-started.md)