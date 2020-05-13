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
ms.openlocfilehash: 6417be4ab7c74d885edffad41085edca27bcf1ce
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378581"
---
# <a name="icordebugreferencevaluegetvalue-method"></a><span data-ttu-id="e97ed-102">ICorDebugReferenceValue::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="e97ed-102">ICorDebugReferenceValue::GetValue Method</span></span>
<span data-ttu-id="e97ed-103">Başvurulan nesnenin geçerli bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="e97ed-103">Gets the current memory address of the referenced object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e97ed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e97ed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e97ed-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e97ed-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="e97ed-106">dışı `CORDB_ADDRESS`Bu ICorDebugReferenceValue nesnesinin işaret ettiği nesnenin adresini belirten bir değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e97ed-106">[out] A pointer to a `CORDB_ADDRESS` value that specifies the address of the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e97ed-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e97ed-107">Requirements</span></span>  
 <span data-ttu-id="e97ed-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e97ed-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e97ed-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e97ed-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e97ed-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e97ed-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e97ed-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e97ed-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
