---
ms.openlocfilehash: 3506653bfc749ae3d8002715ca72ca89de7a681b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91025221"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="929c2-101">Bir addressHeader öğesi null ise, WCF AddressHeaderCollection şimdi bir ArgumentException oluşturur</span><span class="sxs-lookup"><span data-stu-id="929c2-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

#### <a name="details"></a><span data-ttu-id="929c2-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="929c2-102">Details</span></span>

<span data-ttu-id="929c2-103">.NET Framework 4.7.1 ' den başlayarak, <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> Oluşturucu <xref:System.ArgumentException> öğelerinden biri ise bir tane oluşturur `null` .</span><span class="sxs-lookup"><span data-stu-id="929c2-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is `null`.</span></span> <span data-ttu-id="929c2-104">.NET Framework 4,7 ve önceki sürümlerde, hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="929c2-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="929c2-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="929c2-105">Suggestion</span></span>

<span data-ttu-id="929c2-106">Bu değişiklik ile .NET Framework 4.7.1 veya sonraki bir sürümde uyumluluk sorunlarıyla karşılaşırsanız, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek devre dışı bırakabilirsiniz `<runtime>` :</span><span class="sxs-lookup"><span data-stu-id="929c2-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="929c2-107">Ad</span><span class="sxs-lookup"><span data-stu-id="929c2-107">Name</span></span>    | <span data-ttu-id="929c2-108">Değer</span><span class="sxs-lookup"><span data-stu-id="929c2-108">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="929c2-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="929c2-109">Scope</span></span>   | <span data-ttu-id="929c2-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="929c2-110">Minor</span></span>   |
| <span data-ttu-id="929c2-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="929c2-111">Version</span></span> | <span data-ttu-id="929c2-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="929c2-112">4.7.1</span></span>   |
| <span data-ttu-id="929c2-113">Tür</span><span class="sxs-lookup"><span data-stu-id="929c2-113">Type</span></span>    | <span data-ttu-id="929c2-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="929c2-114">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="929c2-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="929c2-115">Affected APIs</span></span>

- <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>

<!--

#### Affected APIs

- `M:System.ServiceModel.Channels.AddressHeaderCollection.#ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})`

-->
