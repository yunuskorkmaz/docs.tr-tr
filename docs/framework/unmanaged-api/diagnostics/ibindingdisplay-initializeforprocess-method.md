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
ms.openlocfilehash: 8645878132359b6218cd62b1ff707208de53704b
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442156"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="834be-102">IBindingDisplay::InitializeForProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="834be-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="834be-103">[IBindingDisplay](ibindingdisplay-interface.md) nesnesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="834be-103">Initializes the [IBindingDisplay](ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="834be-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="834be-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="834be-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="834be-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="834be-106">'ndaki İşlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="834be-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="834be-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="834be-107">Remarks</span></span>  
 <span data-ttu-id="834be-108">Hata ayıklayıcı, `InitializeForProcess` bağlama görüntüsünü başlatmak için oluşturma zamanında yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="834be-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="834be-109">`InitializeForProcess`üzerinde diğer herhangi bir yöntem çağrılmadan önce oluşturulma zamanında çağrılmalıdır `IBindingDisplay` .</span><span class="sxs-lookup"><span data-stu-id="834be-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="834be-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="834be-110">Requirements</span></span>  
 <span data-ttu-id="834be-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="834be-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="834be-112">**Üst bilgi:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="834be-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="834be-113">**Kitaplık:** BindingDisplay. IDL</span><span class="sxs-lookup"><span data-stu-id="834be-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="834be-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="834be-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="834be-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="834be-115">See also</span></span>

- [<span data-ttu-id="834be-116">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="834be-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
