---
title: ICorDebugAppDomain::GetObject Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ca9792df69f859e20f1d9e40754d1cec138945d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480032"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="bc548-102">ICorDebugAppDomain::GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc548-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="bc548-103">Ortak dil çalışma zamanı (CLR) uygulama etki alanı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="bc548-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc548-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc548-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc548-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc548-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="bc548-106">[out] CLR uygulama etki alanını temsil eden bir Icordebugvalue arabirimi nesnesinin adresine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc548-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc548-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bc548-107">Return Value</span></span>  
 <span data-ttu-id="bc548-108">Yönetilen, <xref:System.AppDomain?displayProperty=nameWithType> nesne henüz oluşturulan bu uygulama etki alanı için yöntem döndürür `S_FALSE` ve yerleştirir `NULL` içinde `*ppObject`.</span><span class="sxs-lookup"><span data-stu-id="bc548-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc548-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc548-109">Remarks</span></span>  
 <span data-ttu-id="bc548-110">Her uygulama etki alanında bir işlem yönetilen sahip <xref:System.AppDomain?displayProperty=nameWithType> temsil ettiği çalışma zamanında nesne.</span><span class="sxs-lookup"><span data-stu-id="bc548-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="bc548-111">Bu işlev yönetilen bu karşılık gelen bir Icordebugvalue arabirimi nesneyi alır <xref:System.AppDomain?displayProperty=nameWithType> nesne.</span><span class="sxs-lookup"><span data-stu-id="bc548-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc548-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc548-112">Requirements</span></span>  
 <span data-ttu-id="bc548-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc548-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc548-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc548-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc548-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc548-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc548-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc548-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
