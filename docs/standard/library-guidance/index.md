---
title: Açık kaynak .NET kitaplık kılavuzu
description: Geliştiricilerin yüksek kaliteli .NET kitaplıkları oluşturması için en iyi uygulama önerileri.
ms.date: 10/17/2018
ms.openlocfilehash: 4c76dfae6ffc39df7f15381be64e33657067d79d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731429"
---
# <a name="open-source-library-guidance"></a><span data-ttu-id="58b85-103">Açık kaynak kitaplık kılavuzu</span><span class="sxs-lookup"><span data-stu-id="58b85-103">Open-source library guidance</span></span>

<span data-ttu-id="58b85-104">Bu kılavuz, geliştiricilerin yüksek kaliteli .NET kitaplıkları oluşturması için öneriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="58b85-104">This guidance provides recommendations for developers to create high-quality .NET libraries.</span></span> <span data-ttu-id="58b85-105">Bu dokümantasyon, bir .NET kitaplığı oluştururken *ne* ve *neden* değil, *nasıl*odaklanır.</span><span class="sxs-lookup"><span data-stu-id="58b85-105">This documentation focuses on the *what* and the *why* when building a .NET library, not the *how*.</span></span>

<span data-ttu-id="58b85-106">Yüksek kaliteli açık kaynak .NET kitaplıklarının yönleri:</span><span class="sxs-lookup"><span data-stu-id="58b85-106">Aspects of high-quality open-source .NET libraries:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="58b85-107">**Kapsayıcı** - İyi .NET kitaplıkları birçok platformu, programlama dilini ve uygulamayı desteklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="58b85-107">**Inclusive** - Good .NET libraries strive to support many platforms, programming languages, and applications.</span></span>
> * <span data-ttu-id="58b85-108">**Kararlı** - İyi .NET kitaplıkları .NET ekosisteminde bir arada bulunur ve birçok kitaplıkla oluşturulmuş uygulamalarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="58b85-108">**Stable** - Good .NET libraries coexist in the .NET ecosystem, running in applications built with many libraries.</span></span>
> * <span data-ttu-id="58b85-109">**Gelişmeye yönelik** - .NET kitaplıkları, mevcut kullanıcıları desteklerken zaman içinde gelişmeli ve gelişmelidir.</span><span class="sxs-lookup"><span data-stu-id="58b85-109">**Designed to evolve** - .NET libraries should improve and evolve over time, while supporting existing users.</span></span>
> * <span data-ttu-id="58b85-110">**Hata ayıklanabilir** - .NET kitaplıkları, kullanıcılar için harika bir hata ayıklama deneyimi oluşturmak için en son araçları kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="58b85-110">**Debuggable** - .NET libraries should use the latest tools to create a great debugging experience for users.</span></span>
> * <span data-ttu-id="58b85-111">**Güvenilen** - .NET kitaplıkları, güvenlik en iyi uygulamalarını kullanarak NuGet'e yayımlayarak geliştiricilerin güvenine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="58b85-111">**Trusted** - .NET libraries have developers' trust by publishing to NuGet using security best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="58b85-112">Başlayın</span><span class="sxs-lookup"><span data-stu-id="58b85-112">Get Started</span></span>](./get-started.md)

## <a name="types-of-recommendations"></a><span data-ttu-id="58b85-113">Öneri türleri</span><span class="sxs-lookup"><span data-stu-id="58b85-113">Types of recommendations</span></span>

<span data-ttu-id="58b85-114">Her makale dört tür öneri sunar: **Do**, **Göz at**, **Kaçın**, ve **etmeyin**.</span><span class="sxs-lookup"><span data-stu-id="58b85-114">Each article presents four types of recommendations: **Do**, **Consider**, **Avoid**, and **Do not**.</span></span> <span data-ttu-id="58b85-115">Öneri türü, ne kadar güçlü bir şekilde izlenmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="58b85-115">The type of recommendation indicates how strongly it should be followed.</span></span>

<span data-ttu-id="58b85-116">Hemen hemen her zaman bir **Do** önerisi takip etmelidir.</span><span class="sxs-lookup"><span data-stu-id="58b85-116">You should almost always follow a **Do** recommendation.</span></span> <span data-ttu-id="58b85-117">Örnek:</span><span class="sxs-lookup"><span data-stu-id="58b85-117">For example:</span></span>

<span data-ttu-id="58b85-118">✔️ DO kitaplığınızı bir NuGet paketi kullanarak dağıtın.</span><span class="sxs-lookup"><span data-stu-id="58b85-118">✔️ DO distribute your library using a NuGet package.</span></span>

<span data-ttu-id="58b85-119">Diğer taraftan, **düşünün** önerileri genellikle takip edilmelidir, ancak kuralın meşru istisnaları vardır ve kılavuzu izlemediğiniz için kendinizi kötü hissetmemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="58b85-119">On the other hand, **Consider** recommendations should generally be followed, but there are legitimate exceptions to the rule and you shouldn't feel bad about not following the guidance:</span></span>

<span data-ttu-id="58b85-120">✔️ NuGet paketinizi kullanmak için [SemVer 2.0.0'ı](https://semver.org/) kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="58b85-120">✔️ CONSIDER using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="58b85-121">Öneriler genellikle iyi bir fikir değildir şeyler söz **kaçının,** ancak kuralı ihlal bazen mantıklı:</span><span class="sxs-lookup"><span data-stu-id="58b85-121">**Avoid** recommendations mention things that are generally not a good idea, but breaking the rule sometimes makes sense:</span></span>

<span data-ttu-id="58b85-122">❌Kaçının NuGet paket başvuruları tam bir sürümünü talep.</span><span class="sxs-lookup"><span data-stu-id="58b85-122">❌ AVOID NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="58b85-123">Ve son olarak, öneriler hemen hemen hiç yapmamanız gereken bir şey gösterir **etmeyin:**</span><span class="sxs-lookup"><span data-stu-id="58b85-123">And finally, **Do not** recommendations indicate something you should almost never do:</span></span>

<span data-ttu-id="58b85-124">❌Kitaplığınızın güçlü adlandırılmış ve güçlü olmayan adlandırılmış sürümlerini yayımlamayın.</span><span class="sxs-lookup"><span data-stu-id="58b85-124">❌ DO NOT publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="58b85-125">Örneğin, `Contoso.Api` ve `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="58b85-125">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="58b85-126">Sonraki</span><span class="sxs-lookup"><span data-stu-id="58b85-126">Next</span></span>](get-started.md)
