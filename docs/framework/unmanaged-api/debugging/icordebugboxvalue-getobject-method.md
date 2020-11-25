---
title: ICorDebugBoxValue::GetObject Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type:
- apiref
ms.openlocfilehash: df151e9fc89214d0851ebe60c7ebdb87224f880c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719092"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="dc9e2-102">ICorDebugBoxValue::GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="dc9e2-102">ICorDebugBoxValue::GetObject Method</span></span>

<span data-ttu-id="dc9e2-103">Kutulanmış değeri alır.</span><span class="sxs-lookup"><span data-stu-id="dc9e2-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc9e2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="dc9e2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc9e2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc9e2-105">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="dc9e2-106">dışı Paketlenmiş değeri temsil eden bir ICorDebugObjectValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dc9e2-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc9e2-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc9e2-107">Requirements</span></span>  

 <span data-ttu-id="dc9e2-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc9e2-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc9e2-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dc9e2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc9e2-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dc9e2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc9e2-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc9e2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
