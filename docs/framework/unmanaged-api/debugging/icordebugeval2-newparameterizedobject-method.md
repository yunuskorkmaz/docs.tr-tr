---
title: "ICorDebugEval2::NewParameterizedObject Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 39b69a82f25ab6df5f2bd2f6dc70caf1bf13a0f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newparameterizedobject-method"></a><span data-ttu-id="fcfaf-102">ICorDebugEval2::NewParameterizedObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fcfaf-102">ICorDebugEval2::NewParameterizedObject Method</span></span>
<span data-ttu-id="fcfaf-103">Yeni bir parametreli türü nesnesi oluşturur ve nesnenin oluşturucusu yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="fcfaf-103">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcfaf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcfaf-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fcfaf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fcfaf-105">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="fcfaf-106">[in] Bir işaretçi ICorDebugFunction nesneye Oluşturucusu örneğinin oluşturulması için nesnesinin temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fcfaf-106">[in] A pointer to an ICorDebugFunction object that represents the constructor of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="fcfaf-107">[in] Tür bağımsız değişkenleri sayıda geçirildi.</span><span class="sxs-lookup"><span data-stu-id="fcfaf-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="fcfaf-108">[in] Her biri noktalarını oluşturulmasını nesne için bir tür bağımsız değişkeni temsil eden bir Icordebugtype nesnesi için bir dizi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="fcfaf-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="fcfaf-109">[in] Oluşturucuya geçirilen bağımsız değişken sayısı.</span><span class="sxs-lookup"><span data-stu-id="fcfaf-109">[in] The number of arguments passed to the constructor.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="fcfaf-110">[in] Oluşturucuya geçirilen bağımsız değişken değeri temsil eden Icordebugvalue nesne işaret her biri bir dizi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="fcfaf-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents an argument value that is passed to the constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcfaf-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fcfaf-111">Remarks</span></span>  
 <span data-ttu-id="fcfaf-112">Nesnenin oluşturucusu sürebilir <xref:System.Type> parametreleri.</span><span class="sxs-lookup"><span data-stu-id="fcfaf-112">The object's constructor may take <xref:System.Type> parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcfaf-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fcfaf-113">Requirements</span></span>  
 <span data-ttu-id="fcfaf-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcfaf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcfaf-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fcfaf-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcfaf-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcfaf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcfaf-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcfaf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
