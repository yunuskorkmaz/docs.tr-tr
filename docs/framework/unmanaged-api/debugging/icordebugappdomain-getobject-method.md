---
description: ': ICorDebugAppDomain:: GetObject yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 59389e2a4ca72f8dcdd7117213e968440d30aaa6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754218"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="599e2-103">ICorDebugAppDomain::GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="599e2-103">ICorDebugAppDomain::GetObject Method</span></span>

<span data-ttu-id="599e2-104">Ortak dil çalışma zamanı (CLR) uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="599e2-104">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="599e2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="599e2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="599e2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="599e2-106">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="599e2-107">dışı CLR uygulama etki alanını temsil eden ICorDebugValue arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="599e2-107">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="599e2-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="599e2-108">Return Value</span></span>  

 <span data-ttu-id="599e2-109"><xref:System.AppDomain?displayProperty=nameWithType>Bu uygulama etki alanı için yönetilen bir nesne oluşturulmadıysa, yöntemi öğesini döndürür `S_FALSE` ve içine koyar `NULL` `*ppObject` .</span><span class="sxs-lookup"><span data-stu-id="599e2-109">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="599e2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="599e2-110">Remarks</span></span>  

 <span data-ttu-id="599e2-111">Bir işlemdeki her uygulama etki alanının <xref:System.AppDomain?displayProperty=nameWithType> kendisini temsil eden çalışma zamanında yönetilen bir nesnesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="599e2-111">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="599e2-112">Bu işlev, bu yönetilen nesneye karşılık gelen bir ICorDebugValue arabirim nesnesi alır <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="599e2-112">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="599e2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="599e2-113">Requirements</span></span>  

 <span data-ttu-id="599e2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="599e2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="599e2-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="599e2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="599e2-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="599e2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="599e2-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="599e2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
