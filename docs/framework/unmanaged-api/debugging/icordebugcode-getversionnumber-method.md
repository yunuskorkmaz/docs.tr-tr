---
title: ICorDebugCode::GetVersionNumber Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetVersionNumber
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cd467f047131bbb078c72db9daca2cbc5a87a7be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="144ff-102">ICorDebugCode::GetVersionNumber Metodu</span><span class="sxs-lookup"><span data-stu-id="144ff-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="144ff-103">Bu "Icordebugcode" temsil eden kodu sürümünü belirleyen tabanlı numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="144ff-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="144ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="144ff-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="144ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="144ff-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="144ff-106">[out] Kod sürüm numarasını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="144ff-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="144ff-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="144ff-107">Remarks</span></span>  
 <span data-ttu-id="144ff-108">Sürüm numarası bir Düzenle ve devam et (Çözücü) işlem kodu gerçekleştirilen her zaman artırılır.</span><span class="sxs-lookup"><span data-stu-id="144ff-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="144ff-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="144ff-109">Requirements</span></span>  
 <span data-ttu-id="144ff-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="144ff-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="144ff-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="144ff-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="144ff-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="144ff-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="144ff-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="144ff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="144ff-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="144ff-114">See Also</span></span>  
 
