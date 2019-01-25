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
ms.openlocfilehash: 563784dd2fe3881cbf3278992ca2c75a94df1d3f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727566"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="4b678-102">IAssemblyEnum::GetNextAssembly Metodu</span><span class="sxs-lookup"><span data-stu-id="4b678-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="4b678-103">Sonraki bir işaretçi alır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) bu konuda yer alan [Iassemblyenum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="4b678-103">Gets a pointer to the next [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contained in this [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b678-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b678-104">Syntax</span></span>  
  
```  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b678-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b678-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="4b678-106">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="4b678-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="4b678-107">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b678-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="4b678-108">[out] Döndürülen `IAssemblyName` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4b678-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4b678-109">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="4b678-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="4b678-110">`dwFlags` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b678-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b678-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b678-111">Requirements</span></span>  
 <span data-ttu-id="4b678-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b678-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b678-113">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4b678-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4b678-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b678-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b678-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b678-115">See also</span></span>
- [<span data-ttu-id="4b678-116">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b678-116">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="4b678-117">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b678-117">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
