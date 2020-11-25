---
title: ICorDebugStringValue::GetString Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetString
helpviewer_keywords:
- ICorDebugStringValue::GetString method [.NET Framework debugging]
- GetString method, ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: 2b94bda7-09ee-435d-91b9-c4e31af1896c
topic_type:
- apiref
ms.openlocfilehash: 9051fa612bef3fbd817ff7bdadbd52c96ade5b7f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697109"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="d6e88-102">ICorDebugStringValue::GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6e88-102">ICorDebugStringValue::GetString Method</span></span>

<span data-ttu-id="d6e88-103">Bu ICorDebugStringValue tarafından başvurulan dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="d6e88-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6e88-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d6e88-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6e88-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6e88-105">Parameters</span></span>  

 `cchString`  
 <span data-ttu-id="d6e88-106">'ndaki `szString` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="d6e88-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="d6e88-107">dışı Dizide döndürülen karakter sayısına yönelik bir işaretçi `szString` .</span><span class="sxs-lookup"><span data-stu-id="d6e88-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="d6e88-108">dışı Alınan dizeyi depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="d6e88-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6e88-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6e88-109">Requirements</span></span>  

 <span data-ttu-id="d6e88-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6e88-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6e88-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d6e88-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6e88-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d6e88-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6e88-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6e88-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
