---
title: 'Risk azaltma: yol Iki nokta denetimleri'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: e88643fea3bd507289436f41880a2de34117884f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457902"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="edb2e-102">Risk azaltma: yol Iki nokta denetimleri</span><span class="sxs-lookup"><span data-stu-id="edb2e-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="edb2e-103">.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, daha önce desteklenmeyen yolları (hem uzunluk hem de biçim bakımından) desteklemeye yönelik bir dizi değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="edb2e-103">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="edb2e-104">Özellikle, uygun sürücü ayırıcı söz dizimini (iki nokta üst üste) denetler.</span><span class="sxs-lookup"><span data-stu-id="edb2e-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="edb2e-105">Etki</span><span class="sxs-lookup"><span data-stu-id="edb2e-105">Impact</span></span>  
 <span data-ttu-id="edb2e-106">Bu değişiklikler <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemlerinin daha önce desteklediği bazı URI yollarını engeller.</span><span class="sxs-lookup"><span data-stu-id="edb2e-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="edb2e-107">Azaltma</span><span class="sxs-lookup"><span data-stu-id="edb2e-107">Mitigation</span></span>  
 <span data-ttu-id="edb2e-108">Artık <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemleri tarafından desteklenmeyen daha önceden kabul edilebilir bir yolun sorununu çözmek için şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="edb2e-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="edb2e-109">Düzeni bir URL 'den el ile kaldırın.</span><span class="sxs-lookup"><span data-stu-id="edb2e-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="edb2e-110">Örneğin, URL 'den `file://` kaldırın.</span><span class="sxs-lookup"><span data-stu-id="edb2e-110">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="edb2e-111">URI 'yi bir <xref:System.Uri> oluşturucusuna geçirin ve <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> özelliğinin değerini alın.</span><span class="sxs-lookup"><span data-stu-id="edb2e-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="edb2e-112">`Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> anahtarını `true`ayarlayarak yeni yol normalleştirmesini geri çevirin.</span><span class="sxs-lookup"><span data-stu-id="edb2e-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="edb2e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edb2e-113">See also</span></span>

- [<span data-ttu-id="edb2e-114">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="edb2e-114">Application compatibility</span></span>](application-compatibility.md)
