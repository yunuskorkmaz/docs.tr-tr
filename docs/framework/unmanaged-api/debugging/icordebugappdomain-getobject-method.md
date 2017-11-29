---
title: ICorDebugAppDomain::GetObject Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetObject
api_location: corguids.lib
api_type: COM
f1_keywords: ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c4f923d8e9bf9762d5208dd6e9be527a50a688b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="e8857-102">ICorDebugAppDomain::GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="e8857-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="e8857-103">Ortak dil çalışma zamanı (CLR) uygulama etki alanı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="e8857-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8857-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8857-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8857-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e8857-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="e8857-106">[out] CLR uygulama etki alanını temsil eden bir Icordebugvalue arabirimi nesnesi adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e8857-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8857-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e8857-107">Return Value</span></span>  
 <span data-ttu-id="e8857-108">Yönetilen varsa <xref:System.AppDomain?displayProperty=nameWithType> nesne kurmadı oluşturulan bu uygulama etki alanı için yöntem `S_FALSE` ve yerleştirir `NULL` içinde `*ppObject`.</span><span class="sxs-lookup"><span data-stu-id="e8857-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8857-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8857-109">Remarks</span></span>  
 <span data-ttu-id="e8857-110">Her uygulama etki alanının bir işlemde bir yönetilen olabilir <xref:System.AppDomain?displayProperty=nameWithType> temsil ettiği çalışma zamanında nesne.</span><span class="sxs-lookup"><span data-stu-id="e8857-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="e8857-111">Bu işlev bu yönetilen karşılık gelen bir Icordebugvalue arabirimi nesneyi alır <xref:System.AppDomain?displayProperty=nameWithType> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e8857-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8857-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8857-112">Requirements</span></span>  
 <span data-ttu-id="e8857-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8857-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8857-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8857-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8857-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8857-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8857-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8857-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
