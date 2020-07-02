---
ms.openlocfilehash: 519de92ca4201d199941afe6382ddf9fc480fbbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614775"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a><span data-ttu-id="e4f6b-101">ServiceBase, OnStart özel durumlarını yaymıyor</span><span class="sxs-lookup"><span data-stu-id="e4f6b-101">ServiceBase doesn't propagate OnStart exceptions</span></span>

#### <a name="details"></a><span data-ttu-id="e4f6b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e4f6b-102">Details</span></span>

<span data-ttu-id="e4f6b-103">.NET Framework 4,7 ve önceki sürümlerde, hizmet başlangıcında oluşturulan özel durumlar, çağıranına yayılmaz <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e4f6b-103">In the .NET Framework 4.7 and earlier versions, exceptions thrown on service startup are not propagated to the caller of <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.</span></span><br/><span data-ttu-id="e4f6b-104">.NET Framework 4.7.1 ' i hedefleyen uygulamalarla başlayarak, çalışma zamanı, <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> başlatılamaz hizmetler için özel durumları yayar.</span><span class="sxs-lookup"><span data-stu-id="e4f6b-104">Starting with applications that target the .NET Framework 4.7.1, the runtime propagates exceptions to <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> for services that fail to start.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e4f6b-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="e4f6b-105">Suggestion</span></span>

<span data-ttu-id="e4f6b-106">Hizmet başlangıcı ' nde, bir özel durum varsa, bu özel durum yayılacaktır.</span><span class="sxs-lookup"><span data-stu-id="e4f6b-106">On service start, if there is an exception, that exception will be propagated.</span></span> <span data-ttu-id="e4f6b-107">Bu, hizmetlerin başlayaamadığı durumların tanılanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e4f6b-107">This should help diagnose cases where services fail to start.</span></span> <br/><span data-ttu-id="e4f6b-108">Bu davranış istenmeyen ise, &lt; &gt; &lt; uygulama yapılandırma dosyanızın çalışma zamanı bölümüne aşağıdaki AppContextSwitchOverrides öğesini ekleyerek devre dışı bırakabilirsiniz &gt; :</span><span class="sxs-lookup"><span data-stu-id="e4f6b-108">If this behavior is undesirable, you can opt out of it by adding the following &lt;AppContextSwitchOverrides&gt; element to the &lt;runtime&gt; section of your application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true" />
```

<span data-ttu-id="e4f6b-109">Uygulamanız 4.7.1 sürümünden önceki bir sürümü hedefliyorsa ancak bu davranışa sahip olmak istiyorsanız, &lt; &gt; &lt; uygulama yapılandırma dosyanızın Runtime bölümüne aşağıdaki AppContextSwitchOverrides öğesini ekleyin &gt; :</span><span class="sxs-lookup"><span data-stu-id="e4f6b-109">If your application targets an earlier version than 4.7.1 but you want to have this behavior, add the following &lt;AppContextSwitchOverrides&gt; element to the &lt;runtime&gt; section of your application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false" />
```

| <span data-ttu-id="e4f6b-110">Name</span><span class="sxs-lookup"><span data-stu-id="e4f6b-110">Name</span></span>    | <span data-ttu-id="e4f6b-111">Değer</span><span class="sxs-lookup"><span data-stu-id="e4f6b-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e4f6b-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e4f6b-112">Scope</span></span>   | <span data-ttu-id="e4f6b-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="e4f6b-113">Minor</span></span>       |
| <span data-ttu-id="e4f6b-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e4f6b-114">Version</span></span> | <span data-ttu-id="e4f6b-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="e4f6b-115">4.7.1</span></span>       |
| <span data-ttu-id="e4f6b-116">Tür</span><span class="sxs-lookup"><span data-stu-id="e4f6b-116">Type</span></span>    | <span data-ttu-id="e4f6b-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="e4f6b-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="e4f6b-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e4f6b-118">Affected APIs</span></span>

- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType>
- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType>
