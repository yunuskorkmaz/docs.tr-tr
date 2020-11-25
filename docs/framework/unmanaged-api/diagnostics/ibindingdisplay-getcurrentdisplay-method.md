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
ms.openlocfilehash: d52f089923d16f93345444c07ff8e0619644f2eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725163"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="168b7-102">IBindingDisplay::GetCurrentDisplay Yöntemi</span><span class="sxs-lookup"><span data-stu-id="168b7-102">IBindingDisplay::GetCurrentDisplay Method</span></span>

<span data-ttu-id="168b7-103">Geçerli bağlama görüntüleme bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="168b7-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="168b7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="168b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="168b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="168b7-105">Parameters</span></span>  

 `display`  
 <span data-ttu-id="168b7-106">[Out, retval] Bağlama görünen bilgilerini içeren bir SAFEARRAY işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="168b7-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="168b7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="168b7-107">Remarks</span></span>  

 <span data-ttu-id="168b7-108">[IBindingDisplay:: InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) yöntemi daha önce başarılı olmalıdır ve program bir hata ayıklayıcı tarafından durdurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="168b7-108">The [IBindingDisplay::InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="168b7-109">Çağıran, `SAFEARRAY` [SafeArrayDestroy](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy)kullanarak döndürülen belleği serbest bırakma olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="168b7-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="168b7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="168b7-110">Requirements</span></span>  

 <span data-ttu-id="168b7-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="168b7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="168b7-112">**Üst bilgi:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="168b7-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="168b7-113">**Kitaplık:** BindingDisplay. IDL</span><span class="sxs-lookup"><span data-stu-id="168b7-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="168b7-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="168b7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="168b7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="168b7-115">See also</span></span>

- [<span data-ttu-id="168b7-116">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="168b7-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
- [<span data-ttu-id="168b7-117">InitializeForProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="168b7-117">InitializeForProcess Method</span></span>](ibindingdisplay-initializeforprocess-method.md)
