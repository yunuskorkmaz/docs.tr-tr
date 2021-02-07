---
description: ': ICorDebugModule:: GetGlobalVariableValue Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugModule::GetGlobalVariableValue Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetGlobalVariableValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetGlobalVariableValue
helpviewer_keywords:
- ICorDebugModule::GetGlobalVariableValue method [.NET Framework debugging]
- GetGlobalVariableValue method [.NET Framework debugging]
ms.assetid: bbc0881c-6a59-41a0-b5ee-2f3d1b71684c
topic_type:
- apiref
ms.openlocfilehash: a4efe2f56387be7351fd5bc16716bcd1f34f7d7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691672"
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="c90b8-103">ICorDebugModule::GetGlobalVariableValue Metodu</span><span class="sxs-lookup"><span data-stu-id="c90b8-103">ICorDebugModule::GetGlobalVariableValue Method</span></span>

<span data-ttu-id="c90b8-104">Belirtilen genel değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="c90b8-104">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c90b8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c90b8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c90b8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c90b8-106">Parameters</span></span>  

 `fieldDef`  
 <span data-ttu-id="c90b8-107">'ndaki `mdFieldDef` Genel değişkeni tanımlayan meta verilere başvuruda bulunan bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="c90b8-107">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c90b8-108">dışı Belirtilen genel değişkenin değerini temsil eden bir ICorDebugValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c90b8-108">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c90b8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c90b8-109">Requirements</span></span>  

 <span data-ttu-id="c90b8-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c90b8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c90b8-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c90b8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c90b8-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c90b8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c90b8-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c90b8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
