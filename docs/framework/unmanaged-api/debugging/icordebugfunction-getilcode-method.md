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
ms.openlocfilehash: ac34fbca56c8a0f00ee3a7e0f898b8ee03287b11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412291"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="ec3a5-102">ICorDebugFunction::GetILCode Metodu</span><span class="sxs-lookup"><span data-stu-id="ec3a5-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="ec3a5-103">Bu ICorDebugFunction nesneyle ilişkili Microsoft Ara dili (MSIL) kodunu temsil eder Icordebugcode örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="ec3a5-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec3a5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec3a5-104">Syntax</span></span>  
  
```  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec3a5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec3a5-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="ec3a5-106">[out] Bir işaretçi `ICorDebugCode` örneği veya işlev MSIL derlenmemiş yoksa null.</span><span class="sxs-lookup"><span data-stu-id="ec3a5-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec3a5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec3a5-107">Remarks</span></span>  
 <span data-ttu-id="ec3a5-108">Düzenle ve devam et izin veriyorsa bu işlevi üzerinde `GetILCode` yöntemi, bu işlevin düzenlenen ortak dil çalışma zamanı (CLR) kodda sürümüne karşılık gelen MSIL kodu alırsınız.</span><span class="sxs-lookup"><span data-stu-id="ec3a5-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec3a5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec3a5-109">Requirements</span></span>  
 <span data-ttu-id="ec3a5-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec3a5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec3a5-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec3a5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec3a5-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec3a5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec3a5-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec3a5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
