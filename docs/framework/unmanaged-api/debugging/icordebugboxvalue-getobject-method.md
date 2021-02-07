---
description: ': ICorDebugBoxValue:: GetObject yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: fc5376fa7ddbbeae3464427b34caf991d0a2f59a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711870"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="76eea-103">ICorDebugBoxValue::GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="76eea-103">ICorDebugBoxValue::GetObject Method</span></span>

<span data-ttu-id="76eea-104">Kutulanmış değeri alır.</span><span class="sxs-lookup"><span data-stu-id="76eea-104">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76eea-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76eea-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76eea-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76eea-106">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="76eea-107">dışı Paketlenmiş değeri temsil eden bir ICorDebugObjectValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="76eea-107">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76eea-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76eea-108">Requirements</span></span>  

 <span data-ttu-id="76eea-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76eea-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76eea-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="76eea-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76eea-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="76eea-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76eea-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76eea-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
