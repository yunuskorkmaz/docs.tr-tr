---
title: 'Azaltma: Yol Kolon Denetimleri'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: c6e1106b6f5d8457417992941b9f28712d484442
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181240"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="ca83c-102">Azaltma: Yol Kolon Denetimleri</span><span class="sxs-lookup"><span data-stu-id="ca83c-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="ca83c-103">.NET Framework 4.6.2'yi hedefleyen uygulamalardan başlayarak, daha önce desteklenmeyen yolları (hem uzunluk hem de biçim açısından) desteklemek için bir dizi değişiklik yapıldı.</span><span class="sxs-lookup"><span data-stu-id="ca83c-103">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="ca83c-104">Özellikle, uygun sürücü ayırıcı sözdizimi (iki nokta üst üste) için denetimler daha doğru yapıldı.</span><span class="sxs-lookup"><span data-stu-id="ca83c-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="ca83c-105">Etki</span><span class="sxs-lookup"><span data-stu-id="ca83c-105">Impact</span></span>  
 <span data-ttu-id="ca83c-106">Bu değişiklikler, daha <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> önce <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> desteklenen bazı URI yollarını ve yöntemleri engeller.</span><span class="sxs-lookup"><span data-stu-id="ca83c-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="ca83c-107">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="ca83c-107">Mitigation</span></span>  
 <span data-ttu-id="ca83c-108">Artık <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> yöntemler ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemler tarafından desteklenen daha önce kabul edilebilir bir yol sorununu çözüme getirmek için aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ca83c-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="ca83c-109">Düzeni bir URL'den el ile kaldırın.</span><span class="sxs-lookup"><span data-stu-id="ca83c-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="ca83c-110">Örneğin, bir `file://` URL'den kaldırın.</span><span class="sxs-lookup"><span data-stu-id="ca83c-110">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="ca83c-111">URI'yi bir <xref:System.Uri> oluşturucuya geçirin ve <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> özelliğin değerini alın.</span><span class="sxs-lookup"><span data-stu-id="ca83c-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="ca83c-112">Anahtarı `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> `true`' ya ayarlayarak yeni yol normalleştirmesi dışında</span><span class="sxs-lookup"><span data-stu-id="ca83c-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ca83c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca83c-113">See also</span></span>

- [<span data-ttu-id="ca83c-114">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="ca83c-114">Application compatibility</span></span>](application-compatibility.md)
