---
title: Mayı Yol noktalı virgül denetimleri
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a74c25a9bf4dd8b9ab86bd280881fe1a7999e1d5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789982"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="e5876-102">Mayı Yol noktalı virgül denetimleri</span><span class="sxs-lookup"><span data-stu-id="e5876-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="e5876-103">.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, daha önce desteklenmeyen yolları (hem uzunluk hem de biçim bakımından) desteklemeye yönelik bir dizi değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e5876-103">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="e5876-104">Özellikle, uygun sürücü ayırıcı söz dizimini (iki nokta üst üste) denetler.</span><span class="sxs-lookup"><span data-stu-id="e5876-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e5876-105">Etki</span><span class="sxs-lookup"><span data-stu-id="e5876-105">Impact</span></span>  
 <span data-ttu-id="e5876-106">Bu değişiklikler, <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemlerinin daha önce desteklediği bazı URI yollarını engeller.</span><span class="sxs-lookup"><span data-stu-id="e5876-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e5876-107">Azaltma</span><span class="sxs-lookup"><span data-stu-id="e5876-107">Mitigation</span></span>  
 <span data-ttu-id="e5876-108">Daha önce <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemleri tarafından desteklenmeyen önceden kabul edilebilir bir yol sorununu geçici olarak çözmek için aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e5876-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="e5876-109">Düzeni bir URL 'den el ile kaldırın.</span><span class="sxs-lookup"><span data-stu-id="e5876-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="e5876-110">Örneğin, bir URL `file://` 'den kaldırın.</span><span class="sxs-lookup"><span data-stu-id="e5876-110">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="e5876-111">URI 'yi bir <xref:System.Uri> oluşturucuya geçirin ve <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> özelliğin değerini alın.</span><span class="sxs-lookup"><span data-stu-id="e5876-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="e5876-112"><xref:System.AppContext> Anahtarı `Switch.System.IO.UseLegacyPathHandling` olarak`true`ayarlayarak yeni yol normalleştirmesini geri çevirin.</span><span class="sxs-lookup"><span data-stu-id="e5876-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e5876-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5876-113">See also</span></span>

- [<span data-ttu-id="e5876-114">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="e5876-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-2.md)
