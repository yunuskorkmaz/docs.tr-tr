---
description: ': ICorDebugModule:: GetClassFromToken Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8184c6c1920a4397c4037160276b5b86033baf71
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722625"
---
# <a name="icordebugmodulegetclassfromtoken-method"></a><span data-ttu-id="80d36-103">ICorDebugModule::GetClassFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80d36-103">ICorDebugModule::GetClassFromToken Method</span></span>

<span data-ttu-id="80d36-104">Meta veri belirteci tarafından belirtilen sınıfı alır.</span><span class="sxs-lookup"><span data-stu-id="80d36-104">Gets the class specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80d36-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80d36-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  mdTypeDef        typeDef,  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80d36-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80d36-106">Parameters</span></span>  

 `typedef`  
 <span data-ttu-id="80d36-107">'ndaki `mdTypeDef` Bir sınıfın meta verilerine başvuran bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="80d36-107">[in] An `mdTypeDef` metadata token that references the metadata of a class.</span></span>  
  
 `ppClass`  
 <span data-ttu-id="80d36-108">dışı Sınıfını temsil eden ICorDebugClass nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="80d36-108">[out] A pointer to the address of an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80d36-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80d36-109">Requirements</span></span>  

 <span data-ttu-id="80d36-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80d36-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80d36-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="80d36-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80d36-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="80d36-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80d36-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80d36-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
