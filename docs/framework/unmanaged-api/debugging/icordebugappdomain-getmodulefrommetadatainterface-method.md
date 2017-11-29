---
title: ICorDebugAppDomain::GetModuleFromMetaDataInterface Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetModuleFromMetaDataInterface
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::GetModuleFromMetaDataInterface
helpviewer_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDatainterface method [.NET Framework debugging]
- GetModuleFromMetaDatainterface method [.NET Framework debugging]
ms.assetid: f35225b3-5dda-4d5a-913d-b3373e9ab81e
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 69b1d7d02031e23571a7a5d0e5c64e6bea66d636
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomaingetmodulefrommetadatainterface-method"></a><span data-ttu-id="46ce5-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="46ce5-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface Method</span></span>
<span data-ttu-id="46ce5-103">Belirtilen meta veriler arabirimine karşılık gelen modülü alır.</span><span class="sxs-lookup"><span data-stu-id="46ce5-103">Gets the module that corresponds to the given metadata interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46ce5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46ce5-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromMetaDataInterface (  
    [in] IUnknown           *pIMetaData,  
    [out] ICorDebugModule  **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46ce5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46ce5-105">Parameters</span></span>  
 `pIMetaData`  
 <span data-ttu-id="46ce5-106">[in] Biri olan bir nesne için bir işaretçi [meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="46ce5-106">[in] A pointer to an object that is one of the [Metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
 `ppModule`  
 <span data-ttu-id="46ce5-107">[out] Bir işaretçi adresine Icordebugmodule nesnenin karşılık gelen modül için belirtilen meta veriler arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="46ce5-107">[out] A pointer to the address of an ICorDebugModule object that represents the module corresponding to the given metadata interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46ce5-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46ce5-108">Requirements</span></span>  
 <span data-ttu-id="46ce5-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46ce5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46ce5-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46ce5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46ce5-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46ce5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46ce5-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46ce5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
