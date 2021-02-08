---
description: ': ICorDebugType:: GetRank metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e13416856f900846d2df4b8a39303cf0b6a48ebc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800909"
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="fb0b8-103">ICorDebugType::GetRank Metodu</span><span class="sxs-lookup"><span data-stu-id="fb0b8-103">ICorDebugType::GetRank Method</span></span>

<span data-ttu-id="fb0b8-104">Bir dizi türündeki boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="fb0b8-104">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb0b8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb0b8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb0b8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb0b8-106">Parameters</span></span>  

 `pnRank`  
 <span data-ttu-id="fb0b8-107">dışı Boyut sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fb0b8-107">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb0b8-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb0b8-108">Requirements</span></span>  

 <span data-ttu-id="fb0b8-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb0b8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb0b8-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fb0b8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb0b8-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fb0b8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb0b8-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb0b8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
