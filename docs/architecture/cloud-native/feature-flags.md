---
title: Özellik bayrakları
description: Azure uygulama yapılandırma özelliğinden yararlanarak bulutta yerel uygulamalarda Özellik bayraklarını uygulama
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 607bd14a415a25b382f550e697542cf749a21772
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614077"
---
# <a name="feature-flags"></a><span data-ttu-id="4328b-103">Özellik bayrakları</span><span class="sxs-lookup"><span data-stu-id="4328b-103">Feature flags</span></span>

<span data-ttu-id="4328b-104">Bölüm 1 ' de, bulut yerelin hız ve çeviklik hakkında çok daha fazla olduğunu belirledik.</span><span class="sxs-lookup"><span data-stu-id="4328b-104">In chapter 1, we affirmed that cloud native is much about speed and agility.</span></span> <span data-ttu-id="4328b-105">Kullanıcılar hızlı yanıt verme, yenilikçi özellikler ve sıfır kapalı kalma süresi bekler.</span><span class="sxs-lookup"><span data-stu-id="4328b-105">Users expect rapid responsiveness, innovative features, and zero downtime.</span></span> <span data-ttu-id="4328b-106">`Feature flags`, bulutta yerel uygulamalar için çevikliği artırmaya yardımcı olan modern bir dağıtım tekniğidir.</span><span class="sxs-lookup"><span data-stu-id="4328b-106">`Feature flags` are a modern deployment technique that helps increase agility for cloud-native applications.</span></span> <span data-ttu-id="4328b-107">Bunlar bir üretim ortamına yeni özellikler dağıtmanızı sağlar, ancak bunların kullanılabilirliğini kısıtlayabilir.</span><span class="sxs-lookup"><span data-stu-id="4328b-107">They enable you to deploy new features into a production environment, but restrict their availability.</span></span> <span data-ttu-id="4328b-108">Bir anahtarın hareketiyle, uygulamayı yeniden başlatmadan veya yeni kod dağıtmaya gerek kalmadan, belirli kullanıcılar için yeni bir özelliği etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4328b-108">With the flick of a switch, you can activate a new feature for specific users without restarting the app or deploying new code.</span></span> <span data-ttu-id="4328b-109">Yeni özelliklerin serbest bırakılması, kod dağıtımlarından ayrıdır.</span><span class="sxs-lookup"><span data-stu-id="4328b-109">They separate the release of new features from their code deployment.</span></span>

<span data-ttu-id="4328b-110">Özellik bayrakları, çalışma zamanında kullanıcılar için işlevselliğin görünürlüğünü denetleyen koşullu mantığa göre oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="4328b-110">Feature flags are built upon conditional logic that control visibility of functionality for users at runtime.</span></span> <span data-ttu-id="4328b-111">Modern bulutta yerel sistemlerde, yeni özellikleri üretime erken dağıtmak, ancak bunları sınırlı bir hedef kitle ile test etmek yaygındır.</span><span class="sxs-lookup"><span data-stu-id="4328b-111">In modern cloud-native systems, it's common to deploy new features into production early, but test them with a limited audience.</span></span> <span data-ttu-id="4328b-112">Güvenirlik arttıkça, özelliği daha geniş kitlelere artımlı olarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="4328b-112">As confidence increases, the feature can be incrementally rolled out to wider audiences.</span></span>

<span data-ttu-id="4328b-113">Özellik bayrakları için diğer kullanım örnekleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="4328b-113">Other use cases for feature flags include:</span></span>

- <span data-ttu-id="4328b-114">Daha yüksek abonelik ücretleri ödemek isteyen özel müşteri gruplarıyla Premium işlevselliği kısıtlayın.</span><span class="sxs-lookup"><span data-stu-id="4328b-114">Restrict premium functionality to specific customer groups willing to pay higher subscription fees.</span></span>
- <span data-ttu-id="4328b-115">Bir sorunu hızla devre dışı bırakarak bir sistemi sabitleyerek geri alma veya anında düzeltme risklerinden kaçının.</span><span class="sxs-lookup"><span data-stu-id="4328b-115">Stabilize a system by quickly deactivating a problem feature, avoiding the risks of a rollback or immediate hotfix.</span></span>
- <span data-ttu-id="4328b-116">Yoğun kullanım dönemlerinde yüksek kaynak tüketimine sahip isteğe bağlı bir özelliği devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="4328b-116">Disable an optional feature with high resource consumption during peak usage periods.</span></span>
- <span data-ttu-id="4328b-117">`experimental feature releases`Uygulanabilirlik ve popülerliği doğrulamak için küçük Kullanıcı kesimlerine geçin.</span><span class="sxs-lookup"><span data-stu-id="4328b-117">Conduct `experimental feature releases` to small user segments to validate feasibility and popularity.</span></span>

<span data-ttu-id="4328b-118">Özellik bayrakları geliştirmeyi de yükseltir `trunk-based` .</span><span class="sxs-lookup"><span data-stu-id="4328b-118">Feature flags also promote `trunk-based` development.</span></span> <span data-ttu-id="4328b-119">Bu, geliştiricilerin tek bir daldaki özelliklerle işbirliği yaptığı, kaynak denetimi dallanan bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="4328b-119">It's a source-control branching model where developers collaborate on features in a single branch.</span></span> <span data-ttu-id="4328b-120">Yaklaşım, uzun süre çalışan çok sayıda özellik dalı birleştirme riskini ve karmaşıklığını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="4328b-120">The approach minimizes the risk and complexity of merging large numbers of long-running feature branches.</span></span> <span data-ttu-id="4328b-121">Özellikler etkinleştirilinceye kadar kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4328b-121">Features are unavailable until activated.</span></span>

## <a name="implementing-feature-flags"></a><span data-ttu-id="4328b-122">Özellik bayraklarını uygulama</span><span class="sxs-lookup"><span data-stu-id="4328b-122">Implementing feature flags</span></span>

<span data-ttu-id="4328b-123">Temel tarafında, özellik bayrağı basit bir başvurudur `decision object` .</span><span class="sxs-lookup"><span data-stu-id="4328b-123">At its core, a feature flag is a reference to a simple `decision object`.</span></span> <span data-ttu-id="4328b-124">Veya Boole durumunu döndürür `on` `off` .</span><span class="sxs-lookup"><span data-stu-id="4328b-124">It returns a Boolean state of `on` or `off`.</span></span> <span data-ttu-id="4328b-125">Bayrak, genellikle bir özellik özelliğini kapsülleyen bir kod bloğunu sarmalar.</span><span class="sxs-lookup"><span data-stu-id="4328b-125">The flag typically wraps a block of code that encapsulates a feature capability.</span></span> <span data-ttu-id="4328b-126">Bayrak durumu, kod bloğunun belirli bir kullanıcı için yürütülüp yürütülmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="4328b-126">The state of the flag determines whether that code block executes for a given user.</span></span> <span data-ttu-id="4328b-127">Şekil 10-11, uygulamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4328b-127">Figure 10-11 shows the implementation.</span></span>

```c#
if (featureFlag) {
    // Run this code block if the featureFlag value is true
} else {
    // Run this code block if the featureFlag value is false
}
```

<span data-ttu-id="4328b-128">**Şekil 10-11** -basit özellik bayrağı uygulama.</span><span class="sxs-lookup"><span data-stu-id="4328b-128">**Figure 10-11** - Simple feature flag implementation.</span></span>

<span data-ttu-id="4328b-129">Bu yaklaşımın karar mantığını Özellik kodundan nasıl ayırdığına göz önünde.</span><span class="sxs-lookup"><span data-stu-id="4328b-129">Note how this approach separates the decision logic from the feature code.</span></span>

<span data-ttu-id="4328b-130">Bölüm 1 ' de, tartıştık `Twelve-Factor App` .</span><span class="sxs-lookup"><span data-stu-id="4328b-130">In chapter 1, we discussed the `Twelve-Factor App`.</span></span> <span data-ttu-id="4328b-131">Uygulama yürütülebilir kodundan yapılandırma ayarları dışında tutulması önerilen kılavuz.</span><span class="sxs-lookup"><span data-stu-id="4328b-131">The guidance recommended keeping configuration settings external from application executable code.</span></span> <span data-ttu-id="4328b-132">Gerektiğinde, ayarlar dış kaynaktan okunabilir.</span><span class="sxs-lookup"><span data-stu-id="4328b-132">When needed, settings can be read in from the external source.</span></span> <span data-ttu-id="4328b-133">Özellik bayrağı yapılandırma değerleri, kod tabanlarından da bağımsız olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4328b-133">Feature flag configuration values should also be independent from their codebase.</span></span> <span data-ttu-id="4328b-134">Ayrı bir depoda ayırıcı bayrağı yapılandırması yaparak, uygulamayı değiştirmeden ve yeniden dağıtmaya gerek kalmadan bayrak durumunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4328b-134">By externalizing flag configuration in a separate repository, you can change flag state without modifying and redeploying the application.</span></span>

<span data-ttu-id="4328b-135">[Azure Uygulama yapılandırması](https://docs.microsoft.com/azure/azure-app-configuration/overview) , özellik bayrakları için merkezi bir depo sağlar.</span><span class="sxs-lookup"><span data-stu-id="4328b-135">[Azure App Configuration](https://docs.microsoft.com/azure/azure-app-configuration/overview) provides a centralized repository for feature flags.</span></span> <span data-ttu-id="4328b-136">Bununla birlikte, farklı türlerde özellik bayrakları tanımlarsınız ve durumlarını hızla ve güvenle işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4328b-136">With it, you define different kinds of feature flags and manipulate their states quickly and confidently.</span></span> <span data-ttu-id="4328b-137">Özellik bayrağı işlevselliğini etkinleştirmek için uygulama yapılandırması istemci kitaplıklarını uygulamanıza eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="4328b-137">You add the App Configuration client libraries to your application to enable feature flag functionality.</span></span> <span data-ttu-id="4328b-138">Çeşitli programlama dili çerçeveleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4328b-138">Various programming language frameworks are supported.</span></span>

<span data-ttu-id="4328b-139">Özellik bayrakları, [ASP.NET Core hizmetinde](https://docs.microsoft.com/azure/azure-app-configuration/use-feature-flags-dotnet-core)kolayca uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="4328b-139">Feature flags can be easily implemented in an [ASP.NET Core service](https://docs.microsoft.com/azure/azure-app-configuration/use-feature-flags-dotnet-core).</span></span> <span data-ttu-id="4328b-140">.NET özellik yönetimi kitaplıklarını ve uygulama yapılandırma sağlayıcısını yüklemek, kodunuzun özelliklerine bildirimli olarak özellik bayrakları eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4328b-140">Installing the .NET Feature Management libraries and App Configuration provider enable you to declaratively add feature flags to your code.</span></span> <span data-ttu-id="4328b-141">Bunlar `FeatureGate` , kod tabanınızda If deyimlerini el ile yazmanız gerekmiyorsa öznitelikleri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="4328b-141">They enable `FeatureGate` attributes so that you don't have to manually write if statements across your codebase.</span></span>

<span data-ttu-id="4328b-142">Başlangıç sınıfınıza yapılandırıldıktan sonra, denetleyiciye, eyleme veya ara yazılım düzeyine Özellik bayrağı işlevi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4328b-142">Once configured in your Startup class, you can add feature flag functionality at the controller, action, or middleware level.</span></span> <span data-ttu-id="4328b-143">Şekil 10-12, denetleyici ve eylem uygulamasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="4328b-143">Figure 10-12 presents controller and action implementation:</span></span>

```c#
[FeatureGate(MyFeatureFlags.FeatureA)]
public class ProductController : Controller
{
    ...
}
```

```c#
[FeatureGate(MyFeatureFlags.FeatureA)]
public IActionResult UpdateProductStatus()
{
    return ObjectResult(ProductDto);
}
```

<span data-ttu-id="4328b-144">**Şekil 10-12** -bir denetleyicide ve eylemde Özellik bayrağı uygulama.</span><span class="sxs-lookup"><span data-stu-id="4328b-144">**Figure 10-12** - Feature flag implementation in a controller and action.</span></span>

<span data-ttu-id="4328b-145">Özellik bayrağı devre dışıysa, Kullanıcı yanıt gövdesi olmayan 404 (bulunamadı) durum kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="4328b-145">If a feature flag is disabled, the user will receive a 404 (Not Found) status code with no response body.</span></span>

<span data-ttu-id="4328b-146">Özellik bayrakları, doğrudan C# sınıflarına eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="4328b-146">Feature flags can also be injected directly into C# classes.</span></span> <span data-ttu-id="4328b-147">Şekil 10-13, özellik bayrağı ekleme işlemini gösterir:</span><span class="sxs-lookup"><span data-stu-id="4328b-147">Figure 10-13 shows feature flag injection:</span></span>

```c#
public class ProductController : Controller
{
    private readonly IFeatureManager _featureManager;

    public ProductController(IFeatureManager featureManager)
    {
        _featureManager = featureManager;
    }
}
```

<span data-ttu-id="4328b-148">**Şekil 10-13** -bir sınıfa Özellik bayrağı ekleme.</span><span class="sxs-lookup"><span data-stu-id="4328b-148">**Figure 10-13** - Feature flag injection into a class.</span></span>

<span data-ttu-id="4328b-149">Özellik Yönetimi kitaplıkları, arka planda Özellik bayrağı yaşam döngüsünü yönetir.</span><span class="sxs-lookup"><span data-stu-id="4328b-149">The Feature Management libraries manage the feature flag lifecycle behind the scenes.</span></span> <span data-ttu-id="4328b-150">Örneğin, yapılandırma deposu için yüksek sayıda çağrıları en aza indirmek için, kitaplıklar belirtilen süre için bayrak belirtir.</span><span class="sxs-lookup"><span data-stu-id="4328b-150">For example, to minimize high numbers of calls to the configuration store, the libraries cache flag states for a specified duration.</span></span> <span data-ttu-id="4328b-151">İstek çağrısı sırasında bayrak durumlarının dengeszliği garanti edebilirler.</span><span class="sxs-lookup"><span data-stu-id="4328b-151">They can guarantee the immutability of flag states during a request call.</span></span> <span data-ttu-id="4328b-152">Ayrıca bir sağlar `Point-in-time snapshot` .</span><span class="sxs-lookup"><span data-stu-id="4328b-152">They also offer a `Point-in-time snapshot`.</span></span> <span data-ttu-id="4328b-153">Herhangi bir anahtar-değer geçmişini yeniden oluşturabilir ve önceki yedi gün içinde herhangi bir anda geçmiş değerini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4328b-153">You can reconstruct the history of any key-value and provide its past value at any moment within the previous seven days.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4328b-154">[Önceki](devops.md) 
> [Sonraki](infrastructure-as-code.md)</span><span class="sxs-lookup"><span data-stu-id="4328b-154">[Previous](devops.md)
[Next](infrastructure-as-code.md)</span></span>
