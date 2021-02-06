---
description: ': ICorDebugType:: GetBase yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugType::GetBase Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
ms.openlocfilehash: 78cd540974b540b704e946f6c723214d72e89ab4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658392"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="a91ef-103">ICorDebugType::GetBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a91ef-103">ICorDebugType::GetBase Method</span></span>

<span data-ttu-id="a91ef-104">Bir ICorDebugType öğesine, varsa, bu tür tarafından temsil edilen türün temel türünü temsil eden bir arabirim işaretçisi alır `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="a91ef-104">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a91ef-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a91ef-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a91ef-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a91ef-106">Parameters</span></span>  

 `pBase`  
 <span data-ttu-id="a91ef-107">dışı `ICorDebugType` Temel türü temsil eden nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a91ef-107">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a91ef-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a91ef-108">Remarks</span></span>  

 <span data-ttu-id="a91ef-109">Bir türün temel türünü aramak, bir nesnenin veya onun üst sınıflarının tüm alanlarını yazdırmak gibi yaygın hata ayıklayıcı işlevselliği uygulamak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a91ef-109">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a91ef-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a91ef-110">Requirements</span></span>  

 <span data-ttu-id="a91ef-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a91ef-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a91ef-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a91ef-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a91ef-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a91ef-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a91ef-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a91ef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
