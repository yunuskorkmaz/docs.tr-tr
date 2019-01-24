---
title: Activate işlevi (WPF yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Acrivate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 4e79b74dc8bb7d57125c27e17e8f52d607fffcf1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722039"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="8eebf-102">Activate işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8eebf-102">Activate Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="8eebf-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="8eebf-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="8eebf-104">Windows Presentation Foundation (WPF) altyapısı tarafından windows yönetimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8eebf-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eebf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8eebf-105">Syntax</span></span>  
  
```cpp  
void Activate(  
    const ActivateParameters* pParameters,  
    __deref_out_ecount(1) LPUNKNOWN* ppInner,  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8eebf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8eebf-106">Parameters</span></span>  
 <span data-ttu-id="8eebf-107">pParameters</span><span class="sxs-lookup"><span data-stu-id="8eebf-107">pParameters</span></span>  
 <span data-ttu-id="8eebf-108">Pencerenin etkinleştirme parametresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8eebf-108">A pointer to the window's activation parameters.</span></span>  
  
 <span data-ttu-id="8eebf-109">ppInner</span><span class="sxs-lookup"><span data-stu-id="8eebf-109">ppInner</span></span>  
 <span data-ttu-id="8eebf-110">Bir işaretçi içeren tek öğeli arabellek adresini bir işaretçiye bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> nesne.</span><span class="sxs-lookup"><span data-stu-id="8eebf-110">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eebf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8eebf-111">Requirements</span></span>  
 <span data-ttu-id="8eebf-112">**Platformlar:** Bkz: [.NET Framework sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eebf-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eebf-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="8eebf-113">**DLL:**</span></span>  
  
 <span data-ttu-id="8eebf-114">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="8eebf-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="8eebf-115">.NET Framework 4 ve üzeri: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="8eebf-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="8eebf-116">**.NET framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eebf-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eebf-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8eebf-117">See also</span></span>
- [<span data-ttu-id="8eebf-118">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8eebf-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
