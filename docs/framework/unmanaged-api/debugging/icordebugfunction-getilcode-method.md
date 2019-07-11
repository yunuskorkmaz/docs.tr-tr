---
title: ICorDebugFunction::GetILCode Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e32ce10b708afa5741d83cbd05f14accb4b2014f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754675"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="cb51a-102">ICorDebugFunction::GetILCode Metodu</span><span class="sxs-lookup"><span data-stu-id="cb51a-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="cb51a-103">ICorDebugFunction Bu nesneyle ilişkili Microsoft Ara dili (MSIL) kodu temsil eden Icordebugcode örneği alır.</span><span class="sxs-lookup"><span data-stu-id="cb51a-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb51a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb51a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb51a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb51a-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="cb51a-106">[out] Bir işaretçi `ICorDebugCode` örneği veya işlevin MSIL derlenmedi yoksa null.</span><span class="sxs-lookup"><span data-stu-id="cb51a-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb51a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb51a-107">Remarks</span></span>  
 <span data-ttu-id="cb51a-108">Düzenle ve devam et izin veriyorsa bu işlev üzerinde `GetILCode` yöntemi, bu işlevin düzenlenen kodu ortak dil çalışma zamanı (CLR) sürümüne karşılık gelen MSIL kodu alırsınız.</span><span class="sxs-lookup"><span data-stu-id="cb51a-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb51a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb51a-109">Requirements</span></span>  
 <span data-ttu-id="cb51a-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb51a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb51a-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb51a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb51a-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb51a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb51a-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb51a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
