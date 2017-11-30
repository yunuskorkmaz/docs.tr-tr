---
title: "ICorDebugAppDomain::IsAttached Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.IsAttached
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a85b674ad705f77e00cf2a8a5286d6a74f7a646
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="02068-102">ICorDebugAppDomain::IsAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02068-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="02068-103">Hata ayıklayıcı uygulama etki alanına bağlı olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="02068-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02068-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02068-104">Syntax</span></span>  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02068-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="02068-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="02068-106">[out] `true` hata ayıklayıcısı ekli uygulama etki alanı için; Aksi takdirde ise `false`.</span><span class="sxs-lookup"><span data-stu-id="02068-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02068-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02068-107">Remarks</span></span>  
 <span data-ttu-id="02068-108">Hata ayıklayıcı uygulama etki alanına ekler kadar Icordebugcontroller yöntemleri kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="02068-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02068-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02068-109">Requirements</span></span>  
 <span data-ttu-id="02068-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02068-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02068-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02068-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02068-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02068-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02068-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02068-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
