---
title: Paylaşılan Web Barındırma için İyileştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: 07a100e2cd6aaff2b54b99144c9d762c8979fb47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140275"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="d400c-102">Paylaşılan Web Barındırma için İyileştirme</span><span class="sxs-lookup"><span data-stu-id="d400c-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="d400c-103">Birkaç küçük Web sitesini barındırarak paylaşılan bir sunucunun yöneticisiyseniz, .NET dizinindeki Aspnet.config dosyasındaki `gcTrimCommitOnLowMemory` `runtime` düğüme aşağıdaki ayarı ekleyerek performansı en iyi duruma getirebilir ve site kapasitesini artırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d400c-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> <span data-ttu-id="d400c-104">Bu ayar yalnızca paylaşılan Web barındırma senaryoları için önerilir.</span><span class="sxs-lookup"><span data-stu-id="d400c-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="d400c-105">Çöp toplayıcı gelecekteki ayırmalar için bellek sakladığından, taahhüt edilen alanı kesinlikle gerekenden daha fazla olabilir.</span><span class="sxs-lookup"><span data-stu-id="d400c-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="d400c-106">Sistem belleğinde ağır bir yük olduğu zamanları karşılamak için bu alanı azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d400c-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="d400c-107">Bu taahhüt edilen alanı azaltmak performansı artırır ve daha fazla siteyi barındırma kapasitesini artırır.</span><span class="sxs-lookup"><span data-stu-id="d400c-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="d400c-108">`gcTrimCommitOnLowMemory` Ayar etkinleştirildiğinde, çöp toplayıcı sistem bellek yükünü değerlendirir ve yük %90'a ulaştığında bir kırpma moduna girer.</span><span class="sxs-lookup"><span data-stu-id="d400c-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="d400c-109">Yük %85'in altına düşene kadar kesme modunu korur.</span><span class="sxs-lookup"><span data-stu-id="d400c-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="d400c-110">Koşullar izin verdiğinde, çöp toplayıcı `gcTrimCommitOnLowMemory` ayarın geçerli uygulamaya yardımcı olmadığına karar verebilir ve bunu yoksayabilir.</span><span class="sxs-lookup"><span data-stu-id="d400c-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d400c-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d400c-111">Example</span></span>  
 <span data-ttu-id="d400c-112">Aşağıdaki XML parçası `gcTrimCommitOnLowMemory` ayarı nasıl etkinleştirecek lerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d400c-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="d400c-113">Elipsler `runtime` düğümde olacak diğer ayarları gösterir.</span><span class="sxs-lookup"><span data-stu-id="d400c-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d400c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d400c-114">See also</span></span>

- [<span data-ttu-id="d400c-115">Çöp Toplama</span><span class="sxs-lookup"><span data-stu-id="d400c-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
