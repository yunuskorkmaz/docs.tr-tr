---
title: ICorDebugType::GetRank Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetRank
helpviewer_keywords:
- GetRank method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetRank method [.NET Framework debugging]
ms.assetid: 72d3d927-f590-4f2d-8f60-448f3dfb96af
topic_type:
- apiref
ms.openlocfilehash: 9a00177faabfcad56d70ec5c64328c90675c1532
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138770"
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="5cb19-102">ICorDebugType::GetRank Metodu</span><span class="sxs-lookup"><span data-stu-id="5cb19-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="5cb19-103">Bir dizi türündeki boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="5cb19-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cb19-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cb19-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cb19-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5cb19-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="5cb19-106">dışı Boyut sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5cb19-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cb19-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5cb19-107">Requirements</span></span>  
 <span data-ttu-id="5cb19-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cb19-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cb19-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5cb19-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cb19-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5cb19-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cb19-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cb19-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
