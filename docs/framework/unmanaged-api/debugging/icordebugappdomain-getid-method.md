---
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
ms.openlocfilehash: 88866d75cc97d40c827359450e8e7bdbe13ef3ab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715895"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="a790b-102">ICorDebugAppDomain::GetId Metodu</span><span class="sxs-lookup"><span data-stu-id="a790b-102">ICorDebugAppDomain::GetId Method</span></span>

<span data-ttu-id="a790b-103">Uygulama etki alanının benzersiz tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="a790b-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a790b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a790b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a790b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a790b-105">Parameters</span></span>  

 `pId`  
 <span data-ttu-id="a790b-106">dışı Uygulama etki alanının benzersiz tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a790b-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a790b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a790b-107">Remarks</span></span>  

 <span data-ttu-id="a790b-108">Uygulama etki alanı için tanımlayıcı, kapsayan işlem içinde benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="a790b-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a790b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a790b-109">Requirements</span></span>  

 <span data-ttu-id="a790b-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a790b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a790b-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a790b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a790b-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a790b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a790b-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a790b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
