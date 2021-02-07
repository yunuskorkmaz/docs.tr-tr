---
description: ': ICorDebugReferenceValue:: GetValue yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 29e0c4997d3349b642381dcf69063de21c3f9330
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691029"
---
# <a name="icordebugreferencevaluegetvalue-method"></a><span data-ttu-id="82642-103">ICorDebugReferenceValue::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="82642-103">ICorDebugReferenceValue::GetValue Method</span></span>

<span data-ttu-id="82642-104">Başvurulan nesnenin geçerli bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="82642-104">Gets the current memory address of the referenced object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82642-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82642-105">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82642-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82642-106">Parameters</span></span>  

 `pValue`  
 <span data-ttu-id="82642-107">dışı `CORDB_ADDRESS` Bu ICorDebugReferenceValue nesnesinin işaret ettiği nesnenin adresini belirten bir değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="82642-107">[out] A pointer to a `CORDB_ADDRESS` value that specifies the address of the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82642-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82642-108">Requirements</span></span>  

 <span data-ttu-id="82642-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82642-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82642-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="82642-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82642-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="82642-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82642-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82642-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
