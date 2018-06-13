---
title: ICorDebugAppDomainEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84ca240f937e210846e6eb9a17abfe70a280b87d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403562"
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="2c1cc-102">ICorDebugAppDomainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c1cc-102">ICorDebugAppDomainEnum::Next Method</span></span>
<span data-ttu-id="2c1cc-103">Uygulama etki alanları belirtilen sayıda geçerli İmleç konumuna başlangıç koleksiyondan alır.</span><span class="sxs-lookup"><span data-stu-id="2c1cc-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c1cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c1cc-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c1cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c1cc-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="2c1cc-106">[in] Alınacak uygulama etki alanları sayısı.</span><span class="sxs-lookup"><span data-stu-id="2c1cc-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="2c1cc-107">[out] Her biri uygulama etki alanını temsil eden bir Icordebugappdomain nesneye işaret eden bir dizi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2c1cc-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="2c1cc-108">[out] Uygulama etki alanları gerçekte döndürülen sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2c1cc-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="2c1cc-109">Bu değer null ise `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="2c1cc-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c1cc-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c1cc-110">Requirements</span></span>  
 <span data-ttu-id="2c1cc-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c1cc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c1cc-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c1cc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c1cc-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c1cc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c1cc-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c1cc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
