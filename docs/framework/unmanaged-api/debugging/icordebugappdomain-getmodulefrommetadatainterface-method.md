---
description: ': ICorDebugAppDomain:: GetModuleFromMetaDataInterface yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 7b0c74bd04024f9f4bf26b5ee8abe18a3a7059e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754244"
---
# <a name="icordebugappdomaingetmodulefrommetadatainterface-method"></a><span data-ttu-id="cbd87-103">ICorDebugAppDomain::GetModuleFromMetaDataInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="cbd87-103">ICorDebugAppDomain::GetModuleFromMetaDataInterface Method</span></span>

<span data-ttu-id="cbd87-104">Verilen meta veri arabirimine karşılık gelen modülü alır.</span><span class="sxs-lookup"><span data-stu-id="cbd87-104">Gets the module that corresponds to the given metadata interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbd87-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbd87-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromMetaDataInterface (  
    [in] IUnknown           *pIMetaData,  
    [out] ICorDebugModule  **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbd87-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cbd87-106">Parameters</span></span>  

 `pIMetaData`  
 <span data-ttu-id="cbd87-107">'ndaki [Meta veri arabirimlerinden](../metadata/metadata-interfaces.md)biri olan nesneye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cbd87-107">[in] A pointer to an object that is one of the [Metadata interfaces](../metadata/metadata-interfaces.md).</span></span>  
  
 `ppModule`  
 <span data-ttu-id="cbd87-108">dışı Belirtilen meta veri arabirimine karşılık gelen modülü temsil eden bir ICorDebugModule nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cbd87-108">[out] A pointer to the address of an ICorDebugModule object that represents the module corresponding to the given metadata interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbd87-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cbd87-109">Requirements</span></span>  

 <span data-ttu-id="cbd87-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbd87-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbd87-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cbd87-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbd87-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cbd87-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbd87-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbd87-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
