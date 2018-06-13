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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f112e0d064041a877963939b78029da08bbbed1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417660"
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="08be1-102">ICorDebugType::GetRank Metodu</span><span class="sxs-lookup"><span data-stu-id="08be1-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="08be1-103">Dimensions sayısı bir dizi türünü alır.</span><span class="sxs-lookup"><span data-stu-id="08be1-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08be1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08be1-104">Syntax</span></span>  
  
```  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08be1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08be1-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="08be1-106">[out] Boyut sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="08be1-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08be1-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08be1-107">Requirements</span></span>  
 <span data-ttu-id="08be1-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08be1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08be1-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08be1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08be1-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08be1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08be1-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08be1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
