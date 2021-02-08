---
description: 'Daha fazla bilgi edinin: Paylaşılan Web barındırma için Iyileştirme'
title: Paylaşılan Web Barındırma için İyileştirme
ms.date: 03/30/2017
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: 80627aba90825fe08f891672da4d598edb6f5686
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782448"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="cfceb-103">Paylaşılan Web Barındırma için İyileştirme</span><span class="sxs-lookup"><span data-stu-id="cfceb-103">Optimization for Shared Web Hosting</span></span>

<span data-ttu-id="cfceb-104">Birkaç küçük Web sitesini barındırarak paylaşılan bir sunucunun yöneticisiyseniz, `gcTrimCommitOnLowMemory` `runtime` .net dizinindeki Aspnet.config dosyasındaki düğümüne aşağıdaki ayarı ekleyerek performansı iyileştirir ve site kapasitesini artırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cfceb-104">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> <span data-ttu-id="cfceb-105">Bu ayar yalnızca paylaşılan web barındırma senaryolarında önerilir.</span><span class="sxs-lookup"><span data-stu-id="cfceb-105">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="cfceb-106">Çöp toplayıcı gelecek ayırmalar için belleği koruduğundan, onun ayrılan alanı kesinlikle gerekenden daha fazla olabilir.</span><span class="sxs-lookup"><span data-stu-id="cfceb-106">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="cfceb-107">Sistem belleğinde ağır bir yük olduğunda bu alanı azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfceb-107">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="cfceb-108">Bu ayrılan alanın azaltılması performansı iyileştirir ve daha fazla siteyi barındırmak için kapasiteyi genişletir.</span><span class="sxs-lookup"><span data-stu-id="cfceb-108">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="cfceb-109">`gcTrimCommitOnLowMemory`Ayar etkinleştirildiğinde, çöp toplayıcı sistem belleği yükünü değerlendirir ve yük %90 ' a ulaştığında bir kırpma modu girer.</span><span class="sxs-lookup"><span data-stu-id="cfceb-109">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="cfceb-110">Yük %85 altına düşene kadar kırpma modunu korur.</span><span class="sxs-lookup"><span data-stu-id="cfceb-110">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="cfceb-111">Koşulların izin vermesi durumunda çöp toplayıcı, `gcTrimCommitOnLowMemory` ayarın geçerli uygulamayı ve yok saymasını sağlamamasına karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="cfceb-111">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfceb-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="cfceb-112">Example</span></span>  

 <span data-ttu-id="cfceb-113">Aşağıdaki XML parçası, ayarı nasıl etkinleştireceğinizi gösterir `gcTrimCommitOnLowMemory` .</span><span class="sxs-lookup"><span data-stu-id="cfceb-113">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="cfceb-114">Üç nokta, düğümde yer alan diğer ayarları gösterir `runtime` .</span><span class="sxs-lookup"><span data-stu-id="cfceb-114">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cfceb-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfceb-115">See also</span></span>

- [<span data-ttu-id="cfceb-116">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="cfceb-116">Garbage Collection</span></span>](index.md)
