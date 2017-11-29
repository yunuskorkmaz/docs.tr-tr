---
title: "Azaltma: Yolu iki nokta üst üste denetimleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a387e02c9d754db6af7fa2d2ba5f2ea6d96d4301
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="5fef2-102">Azaltma: Yolu iki nokta üst üste denetimleri</span><span class="sxs-lookup"><span data-stu-id="5fef2-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="5fef2-103">Hedefleyen uygulamalar ile başlayan [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], daha önce desteklenmeyen yolları (her ikisi de uzunluğu ve biçim açısından) desteklemek için yapılan değişiklik sayısı.</span><span class="sxs-lookup"><span data-stu-id="5fef2-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="5fef2-104">Özellikle, uygun sürücü ayırıcı sözdizimi (iki nokta üst üste) denetler daha doğru yapıldı.</span><span class="sxs-lookup"><span data-stu-id="5fef2-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="5fef2-105">Etki</span><span class="sxs-lookup"><span data-stu-id="5fef2-105">Impact</span></span>  
 <span data-ttu-id="5fef2-106">Bu değişiklikler bazı URI yollarını engellemeye <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> daha önce desteklenen yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="5fef2-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="5fef2-107">Azaltma</span><span class="sxs-lookup"><span data-stu-id="5fef2-107">Mitigation</span></span>  
 <span data-ttu-id="5fef2-108">Artık tarafından desteklenen daha önce kabul edilebilir bir yolu sorunu gidermek için <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemleri, aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5fef2-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
-   <span data-ttu-id="5fef2-109">El ile bir URL'den düzeni kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5fef2-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="5fef2-110">Örneğin, kaldırma `file://` bir URL'den.</span><span class="sxs-lookup"><span data-stu-id="5fef2-110">For example, remove `file://` from a URL.</span></span>  
  
-   <span data-ttu-id="5fef2-111">URI geçirmek bir <xref:System.Uri> oluşturucusu ve değerini almak <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5fef2-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
-   <span data-ttu-id="5fef2-112">Yeni yol normalleştirme dışında ayarlayarak opt `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> geçiş `true`.</span><span class="sxs-lookup"><span data-stu-id="5fef2-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5fef2-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5fef2-113">See Also</span></span>  
 [<span data-ttu-id="5fef2-114">Yeniden hedefleme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="5fef2-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
