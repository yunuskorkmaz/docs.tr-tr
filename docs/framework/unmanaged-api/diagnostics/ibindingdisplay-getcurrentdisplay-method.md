---
title: IBindingDisplay::GetCurrentDisplay Metodu
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 889456f08c967c807b4d3d09508af000035ebdaf
ms.sourcegitcommit: bd4fa78f5a46133efdead1bc692a9aa2811d7868
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42755086"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="734a3-102">IBindingDisplay::GetCurrentDisplay Metodu</span><span class="sxs-lookup"><span data-stu-id="734a3-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="734a3-103">Geçerli bağlama görüntü bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="734a3-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="734a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="734a3-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="734a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="734a3-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="734a3-106">[out, retval] Bağlama görünen bilgileri içeren bir SAFEARRAY'i işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="734a3-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="734a3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="734a3-107">Remarks</span></span>  
 <span data-ttu-id="734a3-108">[Ibindingdisplay::ınitializeforprocess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) yöntemi gerekir daha önce başarılı ve programı bir hata ayıklayıcının durdurulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="734a3-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="734a3-109">Arayan döndürülen serbest `SAFEARRAY` kullanarak bellek [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="734a3-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="734a3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="734a3-110">Requirements</span></span>  
 <span data-ttu-id="734a3-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="734a3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="734a3-112">**Başlık:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="734a3-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="734a3-113">**Kitaplığı:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="734a3-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="734a3-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="734a3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="734a3-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="734a3-115">See Also</span></span>  
 [<span data-ttu-id="734a3-116">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="734a3-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 [<span data-ttu-id="734a3-117">InitializeForProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="734a3-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
