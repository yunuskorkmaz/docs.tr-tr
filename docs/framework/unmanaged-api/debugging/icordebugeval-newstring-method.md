---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgeval:: NewString Yöntemi'
title: ICorDebugEval::NewString Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
ms.openlocfilehash: 21eb49900d84cb1ad1f68a701998a4a778c3ef17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693852"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="00f33-103">ICorDebugEval::NewString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00f33-103">ICorDebugEval::NewString Method</span></span>

<span data-ttu-id="00f33-104">Belirtilen içeriğe sahip yeni bir dize örneği ayırır.</span><span class="sxs-lookup"><span data-stu-id="00f33-104">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00f33-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00f33-105">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00f33-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="00f33-106">Parameters</span></span>  

 `string`  
 <span data-ttu-id="00f33-107">'ndaki Dize için içerik işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="00f33-107">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00f33-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00f33-108">Remarks</span></span>  

 <span data-ttu-id="00f33-109">Dize her zaman iş parçacığının yürütüldüğü uygulama etki alanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="00f33-109">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00f33-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00f33-110">Requirements</span></span>  

 <span data-ttu-id="00f33-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00f33-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00f33-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="00f33-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00f33-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="00f33-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00f33-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00f33-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
