---
title: "İşlevini etkinleştirin (WPF yönetilmeyen API Başvurusu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: Acrivate
api_location: PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d890f3bd69c721071695713e0750180d50ed1ddf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="ba17b-102">İşlevini etkinleştirin (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ba17b-102">Activate Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="ba17b-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="ba17b-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="ba17b-104">Windows Presentation Foundation (WPF) altyapısı tarafından windows yönetimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba17b-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba17b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba17b-105">Syntax</span></span>  
  
```cpp  
void Activate(  
    const ActivateParameters* pParameters,  
    __deref_out_ecount(1) LPUNKNOWN* ppInner,  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba17b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba17b-106">Parameters</span></span>  
 <span data-ttu-id="ba17b-107">pParameters</span><span class="sxs-lookup"><span data-stu-id="ba17b-107">pParameters</span></span>  
 <span data-ttu-id="ba17b-108">Pencerenin etkinleştirme parametresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ba17b-108">A pointer to the window's activation parameters.</span></span>  
  
 <span data-ttu-id="ba17b-109">ppInner</span><span class="sxs-lookup"><span data-stu-id="ba17b-109">ppInner</span></span>  
 <span data-ttu-id="ba17b-110">Bir işaretçi içeren bir tek öğe arabelleği adresini gösteren bir işaretçi bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ba17b-110">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba17b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba17b-111">Requirements</span></span>  
 <span data-ttu-id="ba17b-112">**Platformlar:** bkz [.NET Framework sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba17b-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba17b-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="ba17b-113">**DLL:**</span></span>  
  
 <span data-ttu-id="ba17b-114">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="ba17b-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="ba17b-115">.NET Framework 4 ve üzeri: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="ba17b-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="ba17b-116">**.NET framework sürümü:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba17b-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba17b-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba17b-117">See Also</span></span>  
 [<span data-ttu-id="ba17b-118">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ba17b-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
