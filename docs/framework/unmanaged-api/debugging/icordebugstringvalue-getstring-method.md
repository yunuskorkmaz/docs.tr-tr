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
ms.openlocfilehash: e23133176cbd703a58c92f9bf1ead530b0bbb8a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178508"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="b029a-102">ICorDebugStringValue::GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b029a-102">ICorDebugStringValue::GetString Method</span></span>
<span data-ttu-id="b029a-103">Bu ICorDebugStringValue tarafından başvurulan dize alır.</span><span class="sxs-lookup"><span data-stu-id="b029a-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b029a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b029a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b029a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b029a-105">Parameters</span></span>  
 `cchString`  
 <span data-ttu-id="b029a-106">[içinde] `szString` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="b029a-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="b029a-107">[çıkış] Dizide döndürülen karakter sayısına `szString` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b029a-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="b029a-108">[çıkış] Alınan dizeyi depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="b029a-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b029a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b029a-109">Requirements</span></span>  
 <span data-ttu-id="b029a-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b029a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b029a-111">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b029a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b029a-112">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b029a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b029a-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b029a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
