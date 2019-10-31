---
title: ICorDebugReferenceValue::GetValue Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::GetValue method [.NET Framework debugging]
ms.assetid: 5da07f99-6c70-46ec-b997-5ab6fb7106cd
topic_type:
- apiref
ms.openlocfilehash: 7a2288eb84bd51795995032954e41525c2ce605a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137720"
---
# <a name="icordebugreferencevaluegetvalue-method"></a><span data-ttu-id="e5e14-102">ICorDebugReferenceValue::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="e5e14-102">ICorDebugReferenceValue::GetValue Method</span></span>
<span data-ttu-id="e5e14-103">Başvurulan nesnenin geçerli bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="e5e14-103">Gets the current memory address of the referenced object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5e14-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5e14-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5e14-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5e14-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="e5e14-106">dışı Bu ICorDebugReferenceValue nesnesinin işaret ettiği nesnenin adresini belirten `CORDB_ADDRESS` bir değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e5e14-106">[out] A pointer to a `CORDB_ADDRESS` value that specifies the address of the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5e14-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5e14-107">Requirements</span></span>  
 <span data-ttu-id="e5e14-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5e14-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5e14-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e5e14-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5e14-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e5e14-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5e14-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5e14-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
