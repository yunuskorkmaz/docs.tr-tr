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
ms.openlocfilehash: 6fe8c3266a8c9a52cd1022589cd68485c4326fd1
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442195"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="38452-102">IBindingDisplay::GetCurrentDisplay Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38452-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="38452-103">Geçerli bağlama görüntüleme bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="38452-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38452-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="38452-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38452-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38452-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="38452-106">[Out, retval] Bağlama görünen bilgilerini içeren bir SAFEARRAY işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="38452-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38452-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38452-107">Remarks</span></span>  
 <span data-ttu-id="38452-108">[IBindingDisplay:: InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) yöntemi daha önce başarılı olmalıdır ve program bir hata ayıklayıcı tarafından durdurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="38452-108">The [IBindingDisplay::InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="38452-109">Çağıran, `SAFEARRAY` [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy)kullanarak döndürülen belleği serbest bırakma olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="38452-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38452-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38452-110">Requirements</span></span>  
 <span data-ttu-id="38452-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38452-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38452-112">**Üst bilgi:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="38452-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="38452-113">**Kitaplık:** BindingDisplay. IDL</span><span class="sxs-lookup"><span data-stu-id="38452-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="38452-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38452-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38452-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38452-115">See also</span></span>

- [<span data-ttu-id="38452-116">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38452-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
- [<span data-ttu-id="38452-117">InitializeForProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38452-117">InitializeForProcess Method</span></span>](ibindingdisplay-initializeforprocess-method.md)
