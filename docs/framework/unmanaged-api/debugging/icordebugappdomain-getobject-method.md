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
ms.openlocfilehash: f2c881603cfa0e4b3d2dc8d1e996631b51d1e850
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134710"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="27c04-102">ICorDebugAppDomain::GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27c04-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="27c04-103">Ortak dil çalışma zamanı (CLR) uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="27c04-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27c04-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27c04-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27c04-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27c04-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="27c04-106">dışı CLR uygulama etki alanını temsil eden ICorDebugValue arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="27c04-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27c04-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="27c04-107">Return Value</span></span>  
 <span data-ttu-id="27c04-108">Bu uygulama etki alanı için yönetilen bir <xref:System.AppDomain?displayProperty=nameWithType> nesnesi oluşturulmadıysa, yöntem `S_FALSE` döndürür ve `*ppObject``NULL` koyar.</span><span class="sxs-lookup"><span data-stu-id="27c04-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27c04-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27c04-109">Remarks</span></span>  
 <span data-ttu-id="27c04-110">Bir işlemdeki her uygulama etki alanı, onu temsil eden çalışma zamanında yönetilen bir <xref:System.AppDomain?displayProperty=nameWithType> nesnesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="27c04-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="27c04-111">Bu işlev, bu yönetilen <xref:System.AppDomain?displayProperty=nameWithType> nesnesine karşılık gelen bir ICorDebugValue arabirim nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="27c04-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27c04-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27c04-112">Requirements</span></span>  
 <span data-ttu-id="27c04-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27c04-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27c04-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="27c04-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27c04-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="27c04-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27c04-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27c04-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
