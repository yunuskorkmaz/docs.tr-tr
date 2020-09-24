---
title: Özellik bayrakları
description: Azure uygulama yapılandırma özelliğinden yararlanarak bulutta yerel uygulamalarda Özellik bayraklarını uygulama
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: ee45c9f187b056887ea6dd3a08da508afca51987
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158103"
---
# <a name="feature-flags"></a>Özellik bayrakları

Bölüm 1 ' de, bulut yerelin hız ve çeviklik hakkında çok daha fazla olduğunu belirledik. Kullanıcılar hızlı yanıt verme, yenilikçi özellikler ve sıfır kapalı kalma süresi bekler. `Feature flags` , bulutta yerel uygulamalar için çevikliği artırmaya yardımcı olan modern bir dağıtım tekniğidir. Bunlar bir üretim ortamına yeni özellikler dağıtmanızı sağlar, ancak bunların kullanılabilirliğini kısıtlayabilir. Bir anahtarın hareketiyle, uygulamayı yeniden başlatmadan veya yeni kod dağıtmaya gerek kalmadan, belirli kullanıcılar için yeni bir özelliği etkinleştirebilirsiniz. Yeni özelliklerin serbest bırakılması, kod dağıtımlarından ayrıdır.

Özellik bayrakları, çalışma zamanında kullanıcılar için işlevselliğin görünürlüğünü denetleyen koşullu mantığa göre oluşturulmuştur. Modern bulutta yerel sistemlerde, yeni özellikleri üretime erken dağıtmak, ancak bunları sınırlı bir hedef kitle ile test etmek yaygındır. Güvenirlik arttıkça, özelliği daha geniş kitlelere artımlı olarak alınabilir.

Özellik bayrakları için diğer kullanım örnekleri şunları içerir:

- Daha yüksek abonelik ücretleri ödemek isteyen özel müşteri gruplarıyla Premium işlevselliği kısıtlayın.
- Bir sorunu hızla devre dışı bırakarak bir sistemi sabitleyerek geri alma veya anında düzeltme risklerinden kaçının.
- Yoğun kullanım dönemlerinde yüksek kaynak tüketimine sahip isteğe bağlı bir özelliği devre dışı bırakın.
- `experimental feature releases`Uygulanabilirlik ve popülerliği doğrulamak için küçük Kullanıcı kesimlerine geçin.

Özellik bayrakları geliştirmeyi de yükseltir `trunk-based` . Bu, geliştiricilerin tek bir daldaki özelliklerle işbirliği yaptığı, kaynak denetimi dallanan bir modeldir. Yaklaşım, uzun süre çalışan çok sayıda özellik dalı birleştirme riskini ve karmaşıklığını en aza indirir. Özellikler etkinleştirilinceye kadar kullanılamaz.

## <a name="implementing-feature-flags"></a>Özellik bayraklarını uygulama

Temel tarafında, özellik bayrağı basit bir başvurudur `decision object` . Veya Boole durumunu döndürür `on` `off` . Bayrak, genellikle bir özellik özelliğini kapsülleyen bir kod bloğunu sarmalar. Bayrak durumu, kod bloğunun belirli bir kullanıcı için yürütülüp yürütülmeyeceğini belirler. Şekil 10-11, uygulamayı gösterir.

```csharp
if (featureFlag) {
    // Run this code block if the featureFlag value is true
} else {
    // Run this code block if the featureFlag value is false
}
```

**Şekil 10-11** -basit özellik bayrağı uygulama.

Bu yaklaşımın karar mantığını Özellik kodundan nasıl ayırdığına göz önünde.

Bölüm 1 ' de, tartıştık `Twelve-Factor App` . Uygulama yürütülebilir kodundan yapılandırma ayarları dışında tutulması önerilen kılavuz. Gerektiğinde, ayarlar dış kaynaktan okunabilir. Özellik bayrağı yapılandırma değerleri, kod tabanlarından da bağımsız olmalıdır. Ayrı bir depoda ayırıcı bayrağı yapılandırması yaparak, uygulamayı değiştirmeden ve yeniden dağıtmaya gerek kalmadan bayrak durumunu değiştirebilirsiniz.

[Azure Uygulama yapılandırması](/azure/azure-app-configuration/overview) , özellik bayrakları için merkezi bir depo sağlar. Bununla birlikte, farklı türlerde özellik bayrakları tanımlarsınız ve durumlarını hızla ve güvenle işleyebilirsiniz. Özellik bayrağı işlevselliğini etkinleştirmek için uygulama yapılandırması istemci kitaplıklarını uygulamanıza eklersiniz. Çeşitli programlama dili çerçeveleri desteklenir.

Özellik bayrakları, [ASP.NET Core hizmetinde](/azure/azure-app-configuration/use-feature-flags-dotnet-core)kolayca uygulanabilir. .NET özellik yönetimi kitaplıklarını ve uygulama yapılandırma sağlayıcısını yüklemek, kodunuzun özelliklerine bildirimli olarak özellik bayrakları eklemenizi sağlar. Bunlar `FeatureGate` , kod tabanınızda If deyimlerini el ile yazmanız gerekmiyorsa öznitelikleri etkinleştirir.

Başlangıç sınıfınıza yapılandırıldıktan sonra, denetleyiciye, eyleme veya ara yazılım düzeyine Özellik bayrağı işlevi ekleyebilirsiniz. Şekil 10-12, denetleyici ve eylem uygulamasını gösterir:

```csharp
[FeatureGate(MyFeatureFlags.FeatureA)]
public class ProductController : Controller
{
    ...
}
```

```csharp
[FeatureGate(MyFeatureFlags.FeatureA)]
public IActionResult UpdateProductStatus()
{
    return ObjectResult(ProductDto);
}
```

**Şekil 10-12** -bir denetleyicide ve eylemde Özellik bayrağı uygulama.

Özellik bayrağı devre dışıysa, Kullanıcı yanıt gövdesi olmayan 404 (bulunamadı) durum kodunu alır.

Özellik bayrakları, doğrudan C# sınıflarına eklenebilir. Şekil 10-13, özellik bayrağı ekleme işlemini gösterir:

```csharp
public class ProductController : Controller
{
    private readonly IFeatureManager _featureManager;

    public ProductController(IFeatureManager featureManager)
    {
        _featureManager = featureManager;
    }
}
```

**Şekil 10-13** -bir sınıfa Özellik bayrağı ekleme.

Özellik Yönetimi kitaplıkları, arka planda Özellik bayrağı yaşam döngüsünü yönetir. Örneğin, yapılandırma deposu için yüksek sayıda çağrıları en aza indirmek için, kitaplıklar belirtilen süre için bayrak belirtir. İstek çağrısı sırasında bayrak durumlarının dengeszliği garanti edebilirler. Ayrıca bir sağlar `Point-in-time snapshot` . Herhangi bir anahtar-değer geçmişini yeniden oluşturabilir ve önceki yedi gün içinde herhangi bir anda geçmiş değerini sağlayabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](devops.md) 
> [Sonraki](infrastructure-as-code.md)
