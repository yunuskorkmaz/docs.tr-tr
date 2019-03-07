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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2eaa48dcc7dad2d66f1a60922c94193120b59b32
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481364"
---
# <a name="icordebugappdomaingetmodulefrommetadatainterface-method"></a><span data-ttu-id="559ce-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="559ce-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface Method</span></span>
<span data-ttu-id="559ce-103">Belirtilen meta veriler arabirimine karşılık gelen modülü alır.</span><span class="sxs-lookup"><span data-stu-id="559ce-103">Gets the module that corresponds to the given metadata interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="559ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="559ce-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromMetaDataInterface (  
    [in] IUnknown           *pIMetaData,  
    [out] ICorDebugModule  **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="559ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="559ce-105">Parameters</span></span>  
 `pIMetaData`  
 <span data-ttu-id="559ce-106">[in] Biri olan bir nesneye bir işaretçi [meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="559ce-106">[in] A pointer to an object that is one of the [Metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
 `ppModule`  
 <span data-ttu-id="559ce-107">[out] Bir işaretçi adresine Icordebugmodule nesnenin karşılık gelen bir modül için belirtilen meta veriler arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="559ce-107">[out] A pointer to the address of an ICorDebugModule object that represents the module corresponding to the given metadata interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="559ce-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="559ce-108">Requirements</span></span>  
 <span data-ttu-id="559ce-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="559ce-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="559ce-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="559ce-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="559ce-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="559ce-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="559ce-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="559ce-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
