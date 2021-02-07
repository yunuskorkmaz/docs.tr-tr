---
description: ': ICorDebugFunction:: GetCurrentVersionNumber yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugFunction::GetCurrentVersionNumber Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
ms.openlocfilehash: ccc96755ac74624a00b806e3f569f39f2d6059f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692543"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="ca722-103">ICorDebugFunction::GetCurrentVersionNumber Metodu</span><span class="sxs-lookup"><span data-stu-id="ca722-103">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>

<span data-ttu-id="ca722-104">Bu ICorDebugFunction nesnesi tarafından temsil edilen işlevde yapılan en son düzenlemenin sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="ca722-104">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca722-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca722-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca722-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca722-106">Parameters</span></span>  

 `pnCurrentVersion`  
 <span data-ttu-id="ca722-107">dışı Bu işlevde yapılan en son düzenlemenin sürüm numarası olan bir tamsayı değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ca722-107">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca722-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca722-108">Remarks</span></span>  

 <span data-ttu-id="ca722-109">Bu işlevde yapılan en son düzenlemenin sürüm numarası, işlevin sürüm numarasından daha büyük olabilir.</span><span class="sxs-lookup"><span data-stu-id="ca722-109">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="ca722-110">İşlevin sürüm numarasını almak için [ICorDebugFunction2:: GetVersionNumber](icordebugfunction2-getversionnumber-method.md) yöntemini veya [ICorDebugCode:: GetVersionNumber](icordebugcode-getversionnumber-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca722-110">Use either the [ICorDebugFunction2::GetVersionNumber](icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca722-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca722-111">Requirements</span></span>  

 <span data-ttu-id="ca722-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca722-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca722-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ca722-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca722-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ca722-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca722-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca722-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
