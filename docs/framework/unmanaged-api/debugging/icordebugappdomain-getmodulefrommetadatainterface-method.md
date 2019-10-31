---
title: ICorDebugAppDomain::GetModuleFromMetaDataInterface Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetModuleFromMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDataInterface
helpviewer_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDatainterface method [.NET Framework debugging]
- GetModuleFromMetaDatainterface method [.NET Framework debugging]
ms.assetid: f35225b3-5dda-4d5a-913d-b3373e9ab81e
topic_type:
- apiref
ms.openlocfilehash: c8469c9aa875e7d567229e9949d83083cbe54987
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110351"
---
# <a name="icordebugappdomaingetmodulefrommetadatainterface-method"></a><span data-ttu-id="55cb9-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="55cb9-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface Method</span></span>
<span data-ttu-id="55cb9-103">Verilen meta veri arabirimine karşılık gelen modülü alır.</span><span class="sxs-lookup"><span data-stu-id="55cb9-103">Gets the module that corresponds to the given metadata interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55cb9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55cb9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromMetaDataInterface (  
    [in] IUnknown           *pIMetaData,  
    [out] ICorDebugModule  **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55cb9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="55cb9-105">Parameters</span></span>  
 `pIMetaData`  
 <span data-ttu-id="55cb9-106">'ndaki [Meta veri arabirimlerinden](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)biri olan nesneye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="55cb9-106">[in] A pointer to an object that is one of the [Metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
 `ppModule`  
 <span data-ttu-id="55cb9-107">dışı Belirtilen meta veri arabirimine karşılık gelen modülü temsil eden bir ICorDebugModule nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="55cb9-107">[out] A pointer to the address of an ICorDebugModule object that represents the module corresponding to the given metadata interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55cb9-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55cb9-108">Requirements</span></span>  
 <span data-ttu-id="55cb9-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55cb9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55cb9-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="55cb9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55cb9-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="55cb9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55cb9-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55cb9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
