---
title: ICorDebugModule::GetClassFromToken Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetClassFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetClassFromToken
helpviewer_keywords:
- GetClassFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetClassFromToken method [.NET Framework debugging]
ms.assetid: 622a4d3c-0425-4c54-a7e4-0735377cdad2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 413e56a65f4966467f487787172973834ac4a65a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988084"
---
# <a name="icordebugmodulegetclassfromtoken-method"></a><span data-ttu-id="97fd4-102">ICorDebugModule::GetClassFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97fd4-102">ICorDebugModule::GetClassFromToken Method</span></span>
<span data-ttu-id="97fd4-103">Metaveri belirteci tarafından belirtilen sınıf alır.</span><span class="sxs-lookup"><span data-stu-id="97fd4-103">Gets the class specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97fd4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97fd4-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  mdTypeDef        typeDef,  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97fd4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97fd4-105">Parameters</span></span>  
 `typedef`  
 <span data-ttu-id="97fd4-106">[in] Bir `mdTypeDef` meta veri sınıfının başvuran meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="97fd4-106">[in] An `mdTypeDef` metadata token that references the metadata of a class.</span></span>  
  
 `ppClass`  
 <span data-ttu-id="97fd4-107">[out] Bir işaretçi adresine Icordebugclass nesnenin sınıfını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="97fd4-107">[out] A pointer to the address of an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97fd4-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97fd4-108">Requirements</span></span>  
 <span data-ttu-id="97fd4-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97fd4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97fd4-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97fd4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97fd4-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97fd4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97fd4-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97fd4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
