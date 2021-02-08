---
description: ': IBindingDisplay:: InitializeForProcess yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: cf7f0f4d057659089bd7da173e5fac98a7c00dad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800418"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="9978f-103">IBindingDisplay::InitializeForProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9978f-103">IBindingDisplay::InitializeForProcess Method</span></span>

<span data-ttu-id="9978f-104">[IBindingDisplay](ibindingdisplay-interface.md) nesnesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="9978f-104">Initializes the [IBindingDisplay](ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9978f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9978f-105">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9978f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9978f-106">Parameters</span></span>  

 `pid`  
 <span data-ttu-id="9978f-107">'ndaki İşlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9978f-107">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9978f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9978f-108">Remarks</span></span>  

 <span data-ttu-id="9978f-109">Hata ayıklayıcı, `InitializeForProcess` bağlama görüntüsünü başlatmak için oluşturma zamanında yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="9978f-109">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="9978f-110">`InitializeForProcess` üzerinde diğer herhangi bir yöntem çağrılmadan önce oluşturulma zamanında çağrılmalıdır `IBindingDisplay` .</span><span class="sxs-lookup"><span data-stu-id="9978f-110">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9978f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9978f-111">Requirements</span></span>  

 <span data-ttu-id="9978f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9978f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9978f-113">**Üst bilgi:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="9978f-113">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="9978f-114">**Kitaplık:** BindingDisplay. IDL</span><span class="sxs-lookup"><span data-stu-id="9978f-114">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="9978f-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9978f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9978f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9978f-116">See also</span></span>

- [<span data-ttu-id="9978f-117">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9978f-117">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
