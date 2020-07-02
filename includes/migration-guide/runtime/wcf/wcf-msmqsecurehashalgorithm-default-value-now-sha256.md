---
ms.openlocfilehash: ccdf232d743c9e270b6ed21f698998eb95a97399
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621384"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="f49df-101">WCF MsmqSecureHashAlgorithm varsayılan değeri artık SHA256</span><span class="sxs-lookup"><span data-stu-id="f49df-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="f49df-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f49df-102">Details</span></span>

<span data-ttu-id="f49df-103">.NET Framework 4.7.1 başlayarak, MSMQ iletileri için WCF 'de varsayılan ileti imzalama algoritması SHA256 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f49df-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="f49df-104">.NET Framework 4,7 ve önceki sürümlerde, varsayılan ileti imzalama algoritması SHA1 ' dır.</span><span class="sxs-lookup"><span data-stu-id="f49df-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f49df-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="f49df-105">Suggestion</span></span>

<span data-ttu-id="f49df-106">Bu değişiklik ile .NET Framework 4.7.1 veya sonraki bir sürümde uyumluluk sorunları yaşıyorsanız, app.config dosyanızın bölümüne aşağıdaki satırı ekleyerek değişikliği devre dışı bırakabilirsiniz <code>&lt;runtime&gt;</code> :</span><span class="sxs-lookup"><span data-stu-id="f49df-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="f49df-107">Name</span><span class="sxs-lookup"><span data-stu-id="f49df-107">Name</span></span>    | <span data-ttu-id="f49df-108">Değer</span><span class="sxs-lookup"><span data-stu-id="f49df-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f49df-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="f49df-109">Scope</span></span>   |<span data-ttu-id="f49df-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="f49df-110">Minor</span></span>|
|<span data-ttu-id="f49df-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f49df-111">Version</span></span>|<span data-ttu-id="f49df-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="f49df-112">4.7.1</span></span>|
|<span data-ttu-id="f49df-113">Tür</span><span class="sxs-lookup"><span data-stu-id="f49df-113">Type</span></span>|<span data-ttu-id="f49df-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="f49df-114">Runtime</span></span>|
