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
ms.openlocfilehash: a21f3b36e418bbde5dcb90f25a39dae03fde77c9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895209"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="63758-102">ICorDebugAppDomain::GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63758-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="63758-103">Ortak dil çalışma zamanı (CLR) uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="63758-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63758-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63758-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63758-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63758-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="63758-106">dışı CLR uygulama etki alanını temsil eden ICorDebugValue arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="63758-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63758-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="63758-107">Return Value</span></span>  
 <span data-ttu-id="63758-108">Bu uygulama etki <xref:System.AppDomain?displayProperty=nameWithType> alanı için yönetilen bir nesne oluşturulmadıysa, yöntemi öğesini döndürür `S_FALSE` ve içine `NULL` `*ppObject`koyar.</span><span class="sxs-lookup"><span data-stu-id="63758-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63758-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63758-109">Remarks</span></span>  
 <span data-ttu-id="63758-110">Bir işlemdeki her uygulama etki alanının kendisini temsil eden çalışma <xref:System.AppDomain?displayProperty=nameWithType> zamanında yönetilen bir nesnesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="63758-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="63758-111">Bu işlev, bu yönetilen <xref:System.AppDomain?displayProperty=nameWithType> nesneye karşılık gelen bir ICorDebugValue arabirim nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="63758-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63758-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63758-112">Requirements</span></span>  
 <span data-ttu-id="63758-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63758-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63758-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="63758-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63758-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="63758-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63758-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63758-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
