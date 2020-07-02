---
ms.openlocfilehash: d29be721b50d1c93723b325774a06e86f77dbebf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621387"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="041f3-101">Bir addressHeader öğesi null ise, WCF AddressHeaderCollection şimdi bir ArgumentException oluşturur</span><span class="sxs-lookup"><span data-stu-id="041f3-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

#### <a name="details"></a><span data-ttu-id="041f3-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="041f3-102">Details</span></span>

<span data-ttu-id="041f3-103">.NET Framework 4.7.1 ' den başlayarak, <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> Oluşturucu <xref:System.ArgumentException> öğelerinden biri ise bir tane oluşturur <code>null</code> .</span><span class="sxs-lookup"><span data-stu-id="041f3-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is <code>null</code>.</span></span> <span data-ttu-id="041f3-104">.NET Framework 4,7 ve önceki sürümlerde, hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="041f3-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="041f3-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="041f3-105">Suggestion</span></span>

<span data-ttu-id="041f3-106">Bu değişiklik ile .NET Framework 4.7.1 veya sonraki bir sürümde uyumluluk sorunlarıyla karşılaşırsanız, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek devre dışı bırakabilirsiniz <code>&lt;runtime&gt;</code> ::</span><span class="sxs-lookup"><span data-stu-id="041f3-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config file::</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="041f3-107">Name</span><span class="sxs-lookup"><span data-stu-id="041f3-107">Name</span></span>    | <span data-ttu-id="041f3-108">Değer</span><span class="sxs-lookup"><span data-stu-id="041f3-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="041f3-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="041f3-109">Scope</span></span>   |<span data-ttu-id="041f3-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="041f3-110">Minor</span></span>|
|<span data-ttu-id="041f3-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="041f3-111">Version</span></span>|<span data-ttu-id="041f3-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="041f3-112">4.7.1</span></span>|
|<span data-ttu-id="041f3-113">Tür</span><span class="sxs-lookup"><span data-stu-id="041f3-113">Type</span></span>|<span data-ttu-id="041f3-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="041f3-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="041f3-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="041f3-115">Affected APIs</span></span>

-<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})></li></ul>|
