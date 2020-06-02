---
title: Paylaşılan Web Barındırma için İyileştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: ccaacd44f8aaed9c3178cb94f98b0f58d4d3c7d4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285995"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="9c903-102">Paylaşılan Web Barındırma için İyileştirme</span><span class="sxs-lookup"><span data-stu-id="9c903-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="9c903-103">Birkaç küçük Web sitesini barındırarak paylaşılan bir sunucunun yöneticisiyseniz, `gcTrimCommitOnLowMemory` `runtime` .NET dizinindeki Aspnet. config dosyasındaki düğümüne aşağıdaki ayarı ekleyerek performansı iyileştirir ve site kapasitesini artırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9c903-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> <span data-ttu-id="9c903-104">Bu ayar yalnızca paylaşılan web barındırma senaryolarında önerilir.</span><span class="sxs-lookup"><span data-stu-id="9c903-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="9c903-105">Çöp toplayıcı gelecek ayırmalar için belleği koruduğundan, onun ayrılan alanı kesinlikle gerekenden daha fazla olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c903-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="9c903-106">Sistem belleğinde ağır bir yük olduğunda bu alanı azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c903-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="9c903-107">Bu ayrılan alanın azaltılması performansı iyileştirir ve daha fazla siteyi barındırmak için kapasiteyi genişletir.</span><span class="sxs-lookup"><span data-stu-id="9c903-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="9c903-108">`gcTrimCommitOnLowMemory`Ayar etkinleştirildiğinde, çöp toplayıcı sistem belleği yükünü değerlendirir ve yük %90 ' a ulaştığında bir kırpma modu girer.</span><span class="sxs-lookup"><span data-stu-id="9c903-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="9c903-109">Yük %85 altına düşene kadar kırpma modunu korur.</span><span class="sxs-lookup"><span data-stu-id="9c903-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="9c903-110">Koşulların izin vermesi durumunda çöp toplayıcı, `gcTrimCommitOnLowMemory` ayarın geçerli uygulamayı ve yok saymasını sağlamamasına karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="9c903-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c903-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c903-111">Example</span></span>  
 <span data-ttu-id="9c903-112">Aşağıdaki XML parçası, ayarı nasıl etkinleştireceğinizi gösterir `gcTrimCommitOnLowMemory` .</span><span class="sxs-lookup"><span data-stu-id="9c903-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="9c903-113">Üç nokta, düğümde yer alan diğer ayarları gösterir `runtime` .</span><span class="sxs-lookup"><span data-stu-id="9c903-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c903-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c903-114">See also</span></span>

- [<span data-ttu-id="9c903-115">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="9c903-115">Garbage Collection</span></span>](index.md)
