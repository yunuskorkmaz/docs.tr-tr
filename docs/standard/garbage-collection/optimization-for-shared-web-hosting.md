---
title: Paylaşılan Web Barındırma için İyileştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: affdbb357cac14f258822591c3817c93ce6077f8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915909"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="583c6-102">Paylaşılan Web Barındırma için İyileştirme</span><span class="sxs-lookup"><span data-stu-id="583c6-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="583c6-103">Birkaç küçük Web sitesini barındırarak paylaşılan bir sunucunun yöneticisiyseniz, .net 'teki Aspnet. config dosyasındaki `gcTrimCommitOnLowMemory` `runtime` düğümüne aşağıdaki ayarı ekleyerek performansı iyileştirir ve site kapasitesini artırabilirsiniz. dizinden</span><span class="sxs-lookup"><span data-stu-id="583c6-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> <span data-ttu-id="583c6-104">Bu ayar yalnızca paylaşılan web barındırma senaryolarında önerilir.</span><span class="sxs-lookup"><span data-stu-id="583c6-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="583c6-105">Çöp toplayıcı gelecek ayırmalar için belleği koruduğundan, onun ayrılan alanı kesinlikle gerekenden daha fazla olabilir.</span><span class="sxs-lookup"><span data-stu-id="583c6-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="583c6-106">Sistem belleğinde ağır bir yük olduğunda bu alanı azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="583c6-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="583c6-107">Bu ayrılan alanın azaltılması performansı iyileştirir ve daha fazla siteyi barındırmak için kapasiteyi genişletir.</span><span class="sxs-lookup"><span data-stu-id="583c6-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="583c6-108">`gcTrimCommitOnLowMemory` Ayar etkinleştirildiğinde, çöp toplayıcı sistem belleği yükünü değerlendirir ve yük% 90 ' a ulaştığında bir kırpma modu girer.</span><span class="sxs-lookup"><span data-stu-id="583c6-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="583c6-109">Yük% 85 altına düşene kadar kırpma modunu korur.</span><span class="sxs-lookup"><span data-stu-id="583c6-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="583c6-110">Koşulların izin vermesi durumunda çöp toplayıcı, `gcTrimCommitOnLowMemory` ayarın geçerli uygulamayı ve yok saymasını sağlamamasına karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="583c6-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="583c6-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="583c6-111">Example</span></span>  
 <span data-ttu-id="583c6-112">Aşağıdaki XML parçası, `gcTrimCommitOnLowMemory` ayarı nasıl etkinleştireceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="583c6-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="583c6-113">Üç nokta, `runtime` düğümde yer alan diğer ayarları gösterir.</span><span class="sxs-lookup"><span data-stu-id="583c6-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="583c6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="583c6-114">See also</span></span>

- [<span data-ttu-id="583c6-115">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="583c6-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
