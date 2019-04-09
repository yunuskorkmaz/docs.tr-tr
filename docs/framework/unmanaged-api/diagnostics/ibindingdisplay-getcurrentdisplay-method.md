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
ms.openlocfilehash: 472e06c3a00762a7bb012fbcb525d8e0b3a9271a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162265"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="a33c1-102">IBindingDisplay::GetCurrentDisplay Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a33c1-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="a33c1-103">Geçerli bağlama görüntü bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a33c1-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a33c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a33c1-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a33c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a33c1-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="a33c1-106">[out, retval] Bağlama görünen bilgileri içeren bir SAFEARRAY'i işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a33c1-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a33c1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a33c1-107">Remarks</span></span>  
 <span data-ttu-id="a33c1-108">[Ibindingdisplay::ınitializeforprocess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) yöntemi gerekir daha önce başarılı ve programı bir hata ayıklayıcının durdurulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a33c1-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="a33c1-109">Arayan döndürülen serbest `SAFEARRAY` kullanarak bellek [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="a33c1-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a33c1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a33c1-110">Requirements</span></span>  
 <span data-ttu-id="a33c1-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a33c1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a33c1-112">**Üst bilgi:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="a33c1-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="a33c1-113">**Kitaplığı:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="a33c1-113">**Library:** BindingDisplay.idl</span></span>  
  
 **<span data-ttu-id="a33c1-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="a33c1-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a33c1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a33c1-115">See also</span></span>

- [<span data-ttu-id="a33c1-116">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a33c1-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="a33c1-117">InitializeForProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a33c1-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
