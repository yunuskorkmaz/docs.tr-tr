---
ms.openlocfilehash: 9baca45de1c8994f610815e84fdee8ba3930eb04
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496213"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="87f1a-101">WCF MsmqSecureHashAlgorithm varsayılan değeri artık SHA256</span><span class="sxs-lookup"><span data-stu-id="87f1a-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="87f1a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="87f1a-102">Details</span></span>

<span data-ttu-id="87f1a-103">.NET Framework 4.7.1 başlayarak, MSMQ iletileri için WCF 'de varsayılan ileti imzalama algoritması SHA256 ' dir.</span><span class="sxs-lookup"><span data-stu-id="87f1a-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="87f1a-104">.NET Framework 4,7 ve önceki sürümlerde, varsayılan ileti imzalama algoritması SHA1 ' dır.</span><span class="sxs-lookup"><span data-stu-id="87f1a-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="87f1a-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="87f1a-105">Suggestion</span></span>

<span data-ttu-id="87f1a-106">Bu değişiklik ile .NET Framework 4.7.1 veya sonraki bir sürümde uyumluluk sorunları yaşıyorsanız, app.config dosyanızın bölümüne aşağıdaki satırı ekleyerek değişikliği devre dışı bırakabilirsiniz <code>&lt;runtime&gt;</code> :</span><span class="sxs-lookup"><span data-stu-id="87f1a-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="87f1a-107">Name</span><span class="sxs-lookup"><span data-stu-id="87f1a-107">Name</span></span>    | <span data-ttu-id="87f1a-108">Değer</span><span class="sxs-lookup"><span data-stu-id="87f1a-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="87f1a-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="87f1a-109">Scope</span></span>   |<span data-ttu-id="87f1a-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="87f1a-110">Minor</span></span>|
|<span data-ttu-id="87f1a-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="87f1a-111">Version</span></span>|<span data-ttu-id="87f1a-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="87f1a-112">4.7.1</span></span>|
|<span data-ttu-id="87f1a-113">Tür</span><span class="sxs-lookup"><span data-stu-id="87f1a-113">Type</span></span>|<span data-ttu-id="87f1a-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="87f1a-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="87f1a-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="87f1a-115">Affected APIs</span></span>

<span data-ttu-id="87f1a-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="87f1a-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
