---
title: 'Risk azaltma: yol Iki nokta denetimleri'
description: Uygun sürücü ayırıcı sözdizimi (iki nokta üst üste) için denetimleri desteklemek üzere .NET Framework 4.6.2 ' de yapılan değişiklikler hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: 03f1c7249549aae7e3bef986c97fb5f320fbeb2f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283464"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="9ac71-103">Risk azaltma: yol Iki nokta denetimleri</span><span class="sxs-lookup"><span data-stu-id="9ac71-103">Mitigation: Path Colon Checks</span></span>

<span data-ttu-id="9ac71-104">.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, daha önce desteklenmeyen yolları (hem uzunluk hem de biçim bakımından) desteklemeye yönelik bir dizi değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="9ac71-104">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="9ac71-105">Özellikle, uygun sürücü ayırıcı söz dizimini (iki nokta üst üste) denetler.</span><span class="sxs-lookup"><span data-stu-id="9ac71-105">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="9ac71-106">Etki</span><span class="sxs-lookup"><span data-stu-id="9ac71-106">Impact</span></span>  

 <span data-ttu-id="9ac71-107">Bu değişiklikler, <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemlerinin daha önce DESTEKLEDIĞI bazı URI yollarını engeller.</span><span class="sxs-lookup"><span data-stu-id="9ac71-107">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="9ac71-108">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="9ac71-108">Mitigation</span></span>  

 <span data-ttu-id="9ac71-109">Daha önce ve yöntemleri tarafından desteklenmeyen önceden kabul edilebilir bir yol sorununu geçici olarak çözmek için aşağıdakileri <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> yapabilirsiniz <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="9ac71-109">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="9ac71-110">Düzeni bir URL 'den el ile kaldırın.</span><span class="sxs-lookup"><span data-stu-id="9ac71-110">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="9ac71-111">Örneğin, `file://` BIR URL 'den kaldırın.</span><span class="sxs-lookup"><span data-stu-id="9ac71-111">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="9ac71-112">URI 'yi bir oluşturucuya geçirin <xref:System.Uri> ve özelliğin değerini alın <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9ac71-112">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="9ac71-113">Anahtarı olarak ayarlayarak yeni yol normalleştirmesini geri çevirin `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> `true` .</span><span class="sxs-lookup"><span data-stu-id="9ac71-113">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9ac71-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ac71-114">See also</span></span>

- [<span data-ttu-id="9ac71-115">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="9ac71-115">Application compatibility</span></span>](application-compatibility.md)
