---
description: ': ICorDebugAppDomain:: GetID Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugAppDomain::GetId Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type:
- apiref
ms.openlocfilehash: ea660aa08e93e4ce2d97f1e7ae05b261db91118f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772496"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="1ca1b-103">ICorDebugAppDomain::GetId Metodu</span><span class="sxs-lookup"><span data-stu-id="1ca1b-103">ICorDebugAppDomain::GetId Method</span></span>

<span data-ttu-id="1ca1b-104">Uygulama etki alanının benzersiz tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="1ca1b-104">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ca1b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ca1b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ca1b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ca1b-106">Parameters</span></span>  

 `pId`  
 <span data-ttu-id="1ca1b-107">dışı Uygulama etki alanının benzersiz tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1ca1b-107">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ca1b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ca1b-108">Remarks</span></span>  

 <span data-ttu-id="1ca1b-109">Uygulama etki alanı için tanımlayıcı, kapsayan işlem içinde benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="1ca1b-109">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ca1b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ca1b-110">Requirements</span></span>  

 <span data-ttu-id="1ca1b-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ca1b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ca1b-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1ca1b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ca1b-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1ca1b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ca1b-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ca1b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
