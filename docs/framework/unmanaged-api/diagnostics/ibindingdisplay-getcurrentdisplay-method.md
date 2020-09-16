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
ms.openlocfilehash: db2474741012c4fd1734adafed112821c42c099c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541714"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="d2af9-102">IBindingDisplay::GetCurrentDisplay Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2af9-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="d2af9-103">Geçerli bağlama görüntüleme bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d2af9-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2af9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d2af9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2af9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d2af9-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="d2af9-106">[Out, retval] Bağlama görünen bilgilerini içeren bir SAFEARRAY işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d2af9-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2af9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2af9-107">Remarks</span></span>  
 <span data-ttu-id="d2af9-108">[IBindingDisplay:: InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) yöntemi daha önce başarılı olmalıdır ve program bir hata ayıklayıcı tarafından durdurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d2af9-108">The [IBindingDisplay::InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="d2af9-109">Çağıran, `SAFEARRAY` [SafeArrayDestroy](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy)kullanarak döndürülen belleği serbest bırakma olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d2af9-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2af9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2af9-110">Requirements</span></span>  
 <span data-ttu-id="d2af9-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2af9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2af9-112">**Üst bilgi:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="d2af9-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="d2af9-113">**Kitaplık:** BindingDisplay. IDL</span><span class="sxs-lookup"><span data-stu-id="d2af9-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="d2af9-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2af9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2af9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2af9-115">See also</span></span>

- [<span data-ttu-id="d2af9-116">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2af9-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
- [<span data-ttu-id="d2af9-117">InitializeForProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2af9-117">InitializeForProcess Method</span></span>](ibindingdisplay-initializeforprocess-method.md)
