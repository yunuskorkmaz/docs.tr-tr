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
ms.openlocfilehash: c3c979477f0928c9c3d2a393042867c84df33ecf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571975"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="91450-102">Paylaşılan Web Barındırma için İyileştirme</span><span class="sxs-lookup"><span data-stu-id="91450-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="91450-103">Birkaç küçük Web sitesi barındırma tarafından paylaşılan bir sunucu yöneticisiyseniz, performansı iyileştirmek ve aşağıdakileri ekleyerek site kapasitesini artırmak `gcTrimCommitOnLowMemory` ayarını `runtime` .NET Aspnet.config dosyasında düğümü dizini:</span><span class="sxs-lookup"><span data-stu-id="91450-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  <span data-ttu-id="91450-104">Bu ayar, yalnızca paylaşılan Web barındırma senaryolarında önerilir.</span><span class="sxs-lookup"><span data-stu-id="91450-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="91450-105">Çöp toplayıcı gelecekteki ayırmaları için bellek koruyacağından, kaydedilmiş alan birden çok kesinlikle gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="91450-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="91450-106">Kez yerleştirmek için bu alanı azaltabilir sistem belleği üzerinde ağır bir yük olduğunda.</span><span class="sxs-lookup"><span data-stu-id="91450-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="91450-107">Bu kaydedilmiş alanını azaltma performansını artırır ve daha fazla siteleri barındırmak için kapasite genişletir.</span><span class="sxs-lookup"><span data-stu-id="91450-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="91450-108">Zaman `gcTrimCommitOnLowMemory` ayarı etkinleştirildiğinde, atık toplayıcı sistem bellek yükü değerlendirir ve yük % 90 ulaştığında kırpma moduna girer.</span><span class="sxs-lookup"><span data-stu-id="91450-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="91450-109">% 85 yük altında düşene kadar kırpma modunu korur.</span><span class="sxs-lookup"><span data-stu-id="91450-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="91450-110">Koşullar izin, atık toplayıcı, karar verebilirsiniz `gcTrimCommitOnLowMemory` ayarı değil geçerli uygulama Yardımı ve yok sayın.</span><span class="sxs-lookup"><span data-stu-id="91450-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91450-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="91450-111">Example</span></span>  
 <span data-ttu-id="91450-112">Aşağıdaki XML parçası nasıl etkinleştirileceği gösterilmiştir `gcTrimCommitOnLowMemory` ayarı.</span><span class="sxs-lookup"><span data-stu-id="91450-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="91450-113">Üç nokta içinde olacak diğer ayarları belirtmek `runtime` düğümü.</span><span class="sxs-lookup"><span data-stu-id="91450-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="91450-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="91450-114">See Also</span></span>  
 [<span data-ttu-id="91450-115">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="91450-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
