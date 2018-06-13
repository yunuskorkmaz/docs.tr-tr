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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92df7bbcc2c391dd28f4075a97595762403d8def
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416321"
---
# <a name="icordebugreferencevaluegetvalue-method"></a><span data-ttu-id="65386-102">ICorDebugReferenceValue::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="65386-102">ICorDebugReferenceValue::GetValue Method</span></span>
<span data-ttu-id="65386-103">Başvurulan nesnenin geçerli bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="65386-103">Gets the current memory address of the referenced object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65386-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65386-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65386-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65386-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="65386-106">[out] Bir işaretçi bir `CORDB_ADDRESS` bu Icordebugreferencevalue nesne işaret ettiği nesnesinin adresini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="65386-106">[out] A pointer to a `CORDB_ADDRESS` value that specifies the address of the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65386-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65386-107">Requirements</span></span>  
 <span data-ttu-id="65386-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65386-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65386-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65386-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65386-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65386-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65386-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65386-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
