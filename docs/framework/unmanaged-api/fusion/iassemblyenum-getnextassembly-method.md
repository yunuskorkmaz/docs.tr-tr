---
title: IAssemblyEnum::GetNextAssembly Metodu
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 977336f9ff5e65905018f7f93ade74e27625f514
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430775"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="77ad0-102">IAssemblyEnum::GetNextAssembly Metodu</span><span class="sxs-lookup"><span data-stu-id="77ad0-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="77ad0-103">Bir işaretçi sonraki alır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) bu konuda yer alan [Iassemblyenum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="77ad0-103">Gets a pointer to the next [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contained in this [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77ad0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77ad0-104">Syntax</span></span>  
  
```  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77ad0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77ad0-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="77ad0-106">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="77ad0-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="77ad0-107">`pvReserved` bir null başvuru olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="77ad0-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="77ad0-108">[out] Döndürülen `IAssemblyName` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="77ad0-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="77ad0-109">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="77ad0-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="77ad0-110">`dwFlags` 0 (sıfır) olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="77ad0-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77ad0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77ad0-111">Requirements</span></span>  
 <span data-ttu-id="77ad0-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77ad0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77ad0-113">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="77ad0-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="77ad0-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77ad0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77ad0-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77ad0-115">See Also</span></span>  
 [<span data-ttu-id="77ad0-116">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77ad0-116">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="77ad0-117">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77ad0-117">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
