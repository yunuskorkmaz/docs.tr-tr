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
ms.openlocfilehash: 8e701b49a99b548bbfd0cd6c583b7069bca2142b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711060"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="8f263-102">IBindingDisplay::InitializeForProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f263-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="8f263-103">Başlatır [Ibindingdisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="8f263-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f263-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f263-104">Syntax</span></span>  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f263-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f263-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="8f263-106">[in] İşlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="8f263-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f263-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f263-107">Remarks</span></span>  
 <span data-ttu-id="8f263-108">Hata ayıklayıcı çağrıları `InitializeForProcess` yöntemi oluşturma zamanında bağlama görüntü başlatılamadı.</span><span class="sxs-lookup"><span data-stu-id="8f263-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="8f263-109">`InitializeForProcess` önce başka bir yöntem oluşturma zamanında çağrılmalıdır `IBindingDisplay` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8f263-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f263-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f263-110">Requirements</span></span>  
 <span data-ttu-id="8f263-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f263-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f263-112">**Üst bilgi:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="8f263-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="8f263-113">**Kitaplığı:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="8f263-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="8f263-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f263-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f263-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f263-115">See also</span></span>
- [<span data-ttu-id="8f263-116">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f263-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
