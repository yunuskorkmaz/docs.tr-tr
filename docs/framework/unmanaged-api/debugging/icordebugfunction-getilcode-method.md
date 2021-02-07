---
description: ': ICorDebugFunction:: GetILCode yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3b7bb29a028b189b24d3fbf02edc8190d9989a51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692530"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="7f4cd-103">ICorDebugFunction::GetILCode Metodu</span><span class="sxs-lookup"><span data-stu-id="7f4cd-103">ICorDebugFunction::GetILCode Method</span></span>

<span data-ttu-id="7f4cd-104">Bu ICorDebugFunction nesnesiyle ilişkili Microsoft ara dili (MSIL) kodunu temsil eden ICorDebugCode örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="7f4cd-104">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f4cd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f4cd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f4cd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f4cd-106">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="7f4cd-107">dışı `ICorDebugCode` Işlev MSIL 'e derlenmediği takdirde, örneğin işaretçisi veya null.</span><span class="sxs-lookup"><span data-stu-id="7f4cd-107">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f4cd-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f4cd-108">Remarks</span></span>  

 <span data-ttu-id="7f4cd-109">Bu işlevde Düzenle ve devam et izni verildiyse, `GetILCode` yöntemi, ortak dil çalışma zamanında (CLR) bu işlevin düzenlenmiş sürümüne karşılık gelen MSIL kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="7f4cd-109">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f4cd-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f4cd-110">Requirements</span></span>  

 <span data-ttu-id="7f4cd-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f4cd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f4cd-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7f4cd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f4cd-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7f4cd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f4cd-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f4cd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
