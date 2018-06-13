---
title: ICorDebugStringValue::GetString Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63d3df561a3b48a4b26426235455ef1a074512f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417972"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="3756e-102">ICorDebugStringValue::GetString Metodu</span><span class="sxs-lookup"><span data-stu-id="3756e-102">ICorDebugStringValue::GetString Method</span></span>
<span data-ttu-id="3756e-103">Bu Icordebugstringvalue tarafından başvurulan dize alır.</span><span class="sxs-lookup"><span data-stu-id="3756e-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3756e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3756e-104">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]   
        WCHAR       szString[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3756e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3756e-105">Parameters</span></span>  
 `cchString`  
 <span data-ttu-id="3756e-106">[in] Boyutunu `szString` dizi.</span><span class="sxs-lookup"><span data-stu-id="3756e-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="3756e-107">[out] Döndürülen karakter sayısını gösteren bir işaretçi `szString` dizi.</span><span class="sxs-lookup"><span data-stu-id="3756e-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="3756e-108">[out] Alınan dize depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="3756e-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3756e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3756e-109">Requirements</span></span>  
 <span data-ttu-id="3756e-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3756e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3756e-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3756e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3756e-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3756e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3756e-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3756e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
