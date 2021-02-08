---
description: ': IBindingDisplay:: GetCurrentDisplay Yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 680a91c8025ac3247701c14c23f442da5e304ecb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800428"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="f559e-103">IBindingDisplay::GetCurrentDisplay Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f559e-103">IBindingDisplay::GetCurrentDisplay Method</span></span>

<span data-ttu-id="f559e-104">Geçerli bağlama görüntüleme bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f559e-104">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f559e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f559e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f559e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f559e-106">Parameters</span></span>  

 `display`  
 <span data-ttu-id="f559e-107">[Out, retval] Bağlama görünen bilgilerini içeren bir SAFEARRAY işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f559e-107">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f559e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f559e-108">Remarks</span></span>  

 <span data-ttu-id="f559e-109">[IBindingDisplay:: InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) yöntemi daha önce başarılı olmalıdır ve program bir hata ayıklayıcı tarafından durdurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f559e-109">The [IBindingDisplay::InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="f559e-110">Çağıran, `SAFEARRAY` [SafeArrayDestroy](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy)kullanarak döndürülen belleği serbest bırakma olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f559e-110">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f559e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f559e-111">Requirements</span></span>  

 <span data-ttu-id="f559e-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f559e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f559e-113">**Üst bilgi:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="f559e-113">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="f559e-114">**Kitaplık:** BindingDisplay. IDL</span><span class="sxs-lookup"><span data-stu-id="f559e-114">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="f559e-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f559e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f559e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f559e-116">See also</span></span>

- [<span data-ttu-id="f559e-117">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f559e-117">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
- [<span data-ttu-id="f559e-118">InitializeForProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f559e-118">InitializeForProcess Method</span></span>](ibindingdisplay-initializeforprocess-method.md)
