---
title: IBindingDisplay::GetCurrentDisplay Yöntemi
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
ms.openlocfilehash: 0f9cc44db9c93a8b018d0586bc1faeda7cfbc9bc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498438"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="0f26e-102">IBindingDisplay::GetCurrentDisplay Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f26e-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="0f26e-103">Geçerli bağlama görüntü bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f26e-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f26e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f26e-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f26e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f26e-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="0f26e-106">[out, retval] Bağlama görünen bilgileri içeren bir SAFEARRAY'i işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0f26e-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f26e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f26e-107">Remarks</span></span>  
 <span data-ttu-id="0f26e-108">[Ibindingdisplay::ınitializeforprocess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) yöntemi gerekir daha önce başarılı ve programı bir hata ayıklayıcının durdurulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f26e-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="0f26e-109">Arayan döndürülen serbest `SAFEARRAY` kullanarak bellek [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="0f26e-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f26e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f26e-110">Requirements</span></span>  
 <span data-ttu-id="0f26e-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f26e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f26e-112">**Üst bilgi:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="0f26e-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="0f26e-113">**Kitaplığı:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="0f26e-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="0f26e-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f26e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f26e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f26e-115">See also</span></span>
- [<span data-ttu-id="0f26e-116">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f26e-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="0f26e-117">InitializeForProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f26e-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
