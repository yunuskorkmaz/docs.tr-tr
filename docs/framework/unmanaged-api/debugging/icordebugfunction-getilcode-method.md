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
ms.openlocfilehash: 8c7be2d48a30a9f649c6d86e4edbc10085195b68
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213627"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="0b642-102">ICorDebugFunction::GetILCode Metodu</span><span class="sxs-lookup"><span data-stu-id="0b642-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="0b642-103">Bu ICorDebugFunction nesnesiyle ilişkili Microsoft ara dili (MSIL) kodunu temsil eden ICorDebugCode örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="0b642-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b642-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b642-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b642-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b642-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="0b642-106">dışı `ICorDebugCode`Işlev MSIL 'e derlenmediği takdirde, örneğin işaretçisi veya null.</span><span class="sxs-lookup"><span data-stu-id="0b642-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b642-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b642-107">Remarks</span></span>  
 <span data-ttu-id="0b642-108">Bu işlevde Düzenle ve devam et izni verildiyse, `GetILCode` yöntemi, ortak dil çalışma zamanında (CLR) bu işlevin düzenlenmiş sürümüne karşılık gelen MSIL kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="0b642-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b642-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b642-109">Requirements</span></span>  
 <span data-ttu-id="0b642-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b642-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b642-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0b642-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b642-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0b642-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b642-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b642-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
