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
ms.openlocfilehash: a163667ea7eca1ed817d642efdb8fc4efa2a0651
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676068"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="7f1f7-102">ICorDebugAppDomain::GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f1f7-102">ICorDebugAppDomain::GetObject Method</span></span>

<span data-ttu-id="7f1f7-103">Ortak dil çalışma zamanı (CLR) uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="7f1f7-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f1f7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7f1f7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f1f7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f1f7-105">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="7f1f7-106">dışı CLR uygulama etki alanını temsil eden ICorDebugValue arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7f1f7-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f1f7-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7f1f7-107">Return Value</span></span>  

 <span data-ttu-id="7f1f7-108"><xref:System.AppDomain?displayProperty=nameWithType>Bu uygulama etki alanı için yönetilen bir nesne oluşturulmadıysa, yöntemi öğesini döndürür `S_FALSE` ve içine koyar `NULL` `*ppObject` .</span><span class="sxs-lookup"><span data-stu-id="7f1f7-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f1f7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f1f7-109">Remarks</span></span>  

 <span data-ttu-id="7f1f7-110">Bir işlemdeki her uygulama etki alanının <xref:System.AppDomain?displayProperty=nameWithType> kendisini temsil eden çalışma zamanında yönetilen bir nesnesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="7f1f7-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="7f1f7-111">Bu işlev, bu yönetilen nesneye karşılık gelen bir ICorDebugValue arabirim nesnesi alır <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7f1f7-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f1f7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f1f7-112">Requirements</span></span>  

 <span data-ttu-id="7f1f7-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f1f7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f1f7-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7f1f7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f1f7-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7f1f7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f1f7-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f1f7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
