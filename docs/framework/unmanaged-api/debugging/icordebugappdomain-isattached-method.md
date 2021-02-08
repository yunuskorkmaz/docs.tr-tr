---
description: ': ICorDebugAppDomain:: ısekli yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugAppDomain::IsAttached Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.IsAttached
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type:
- apiref
ms.openlocfilehash: 79427d08be9ffea253695b67767d68589edf6979
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772392"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="06b11-103">ICorDebugAppDomain::IsAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06b11-103">ICorDebugAppDomain::IsAttached Method</span></span>

<span data-ttu-id="06b11-104">Hata ayıklayıcının uygulama etki alanına bağlı olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="06b11-104">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06b11-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06b11-105">Syntax</span></span>  
  
```cpp  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06b11-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06b11-106">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="06b11-107">[out] `true` hata ayıklayıcı uygulama etki alanına eklenmişse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="06b11-107">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06b11-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06b11-108">Remarks</span></span>  

 <span data-ttu-id="06b11-109">ICorDebugController yöntemleri, hata ayıklayıcı uygulama etki alanına iliştirene kadar kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="06b11-109">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06b11-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06b11-110">Requirements</span></span>  

 <span data-ttu-id="06b11-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06b11-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06b11-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="06b11-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06b11-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="06b11-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06b11-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06b11-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
