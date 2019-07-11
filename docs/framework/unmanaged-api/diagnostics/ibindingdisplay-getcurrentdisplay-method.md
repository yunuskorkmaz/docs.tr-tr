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
ms.openlocfilehash: d075aeeb904469613999829a1444511d069b9918
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775973"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="b0779-102">IBindingDisplay::GetCurrentDisplay Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0779-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="b0779-103">Geçerli bağlama görüntü bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b0779-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0779-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0779-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0779-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0779-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="b0779-106">[out, retval] Bağlama görünen bilgileri içeren bir SAFEARRAY'i işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b0779-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0779-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0779-107">Remarks</span></span>  
 <span data-ttu-id="b0779-108">[Ibindingdisplay::ınitializeforprocess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) yöntemi gerekir daha önce başarılı ve programı bir hata ayıklayıcının durdurulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0779-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="b0779-109">Arayan döndürülen serbest `SAFEARRAY` kullanarak bellek [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="b0779-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0779-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0779-110">Requirements</span></span>  
 <span data-ttu-id="b0779-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0779-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0779-112">**Üst bilgi:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="b0779-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="b0779-113">**Kitaplığı:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="b0779-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="b0779-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0779-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0779-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0779-115">See also</span></span>

- [<span data-ttu-id="b0779-116">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0779-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="b0779-117">InitializeForProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0779-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
