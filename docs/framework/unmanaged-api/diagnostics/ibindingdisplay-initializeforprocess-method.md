---
title: "IBindingDisplay::InitializeForProcess Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IBindingDisplay.InitializeForProcess
api_location: diasymreader.dll
api_type: COM
f1_keywords: IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e5ab3bb38d23e5841a347a348a09deb3b5639962
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="31e5e-102">IBindingDisplay::InitializeForProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31e5e-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="31e5e-103">Başlatır [Ibindingdisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="31e5e-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31e5e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31e5e-104">Syntax</span></span>  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31e5e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31e5e-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="31e5e-106">[in] İşlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="31e5e-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31e5e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31e5e-107">Remarks</span></span>  
 <span data-ttu-id="31e5e-108">Hata ayıklayıcı çağrıları `InitializeForProcess` yöntemi oluşturma zamanında bağlama görüntü başlatılamadı.</span><span class="sxs-lookup"><span data-stu-id="31e5e-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="31e5e-109">`InitializeForProcess`önce başka bir yöntem oluşturma zamanında üzerinde çağrılmalıdır `IBindingDisplay` olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="31e5e-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31e5e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31e5e-110">Requirements</span></span>  
 <span data-ttu-id="31e5e-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31e5e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31e5e-112">**Başlık:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="31e5e-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="31e5e-113">**Kitaplığı:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="31e5e-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="31e5e-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31e5e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31e5e-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31e5e-115">See Also</span></span>  
 [<span data-ttu-id="31e5e-116">Ibindingdisplay arabirimi</span><span class="sxs-lookup"><span data-stu-id="31e5e-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
