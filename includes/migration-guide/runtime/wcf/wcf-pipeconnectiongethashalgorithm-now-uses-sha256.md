---
ms.openlocfilehash: 71f61f23a8b17459610d253766a99e594f09428e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857240"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="1b202-101">WCF PipeConnection.GetHashAlgorithm SHA256 artık kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b202-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1b202-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1b202-102">Details</span></span>|<span data-ttu-id="1b202-103">.NET Framework 4.7.1 ile başlayarak, Windows Communication Foundation SHA256 karma rastgele adları için adlandırılmış kanallar oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b202-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="1b202-104">.NET Framework 4.7 ve önceki sürümlerinde SHA1 karması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b202-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>|
|<span data-ttu-id="1b202-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="1b202-105">Suggestion</span></span>|<span data-ttu-id="1b202-106">.NET Framework 4.7.1 Bu değişiklik ile uyumluluk sorunu içine çalıştırın ya da daha sonra bunu aşağıdaki satırı ekleyerek çevirme <code>&lt;runtime&gt;</code> app.config dosyanıza bölümünü:</span><span class="sxs-lookup"><span data-stu-id="1b202-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="1b202-107">`Scope`</span><span class="sxs-lookup"><span data-stu-id="1b202-107">Scope</span></span>|<span data-ttu-id="1b202-108">Küçük</span><span class="sxs-lookup"><span data-stu-id="1b202-108">Minor</span></span>|
|<span data-ttu-id="1b202-109">Version</span><span class="sxs-lookup"><span data-stu-id="1b202-109">Version</span></span>|<span data-ttu-id="1b202-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="1b202-110">4.7.1</span></span>|
|<span data-ttu-id="1b202-111">Type</span><span class="sxs-lookup"><span data-stu-id="1b202-111">Type</span></span>|<span data-ttu-id="1b202-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="1b202-112">Runtime</span></span>|

