---
title: IBindingDisplay::InitializeForProcess Yöntemi
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa1e85751f90c34d40e88207af5c7eed2dd1bb82
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599370"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="c2d1f-102">IBindingDisplay::InitializeForProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2d1f-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="c2d1f-103">Başlatır [Ibindingdisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="c2d1f-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2d1f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2d1f-104">Syntax</span></span>  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2d1f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2d1f-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="c2d1f-106">[in] İşlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c2d1f-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2d1f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2d1f-107">Remarks</span></span>  
 <span data-ttu-id="c2d1f-108">Hata ayıklayıcı çağrıları `InitializeForProcess` yöntemi oluşturma zamanında bağlama görüntü başlatılamadı.</span><span class="sxs-lookup"><span data-stu-id="c2d1f-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="c2d1f-109">`InitializeForProcess` önce başka bir yöntem oluşturma zamanında çağrılmalıdır `IBindingDisplay` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c2d1f-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2d1f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2d1f-110">Requirements</span></span>  
 <span data-ttu-id="c2d1f-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2d1f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2d1f-112">**Üst bilgi:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="c2d1f-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="c2d1f-113">**Kitaplığı:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="c2d1f-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="c2d1f-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2d1f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d1f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2d1f-115">See also</span></span>

- [<span data-ttu-id="c2d1f-116">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2d1f-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
