---
title: ICorDebugAppDomain2::GetArrayOrPointerType Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain2.GetArrayOrPointerType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c08a56ff7f6bd109c5568a7f992850708a22a4b0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="20f7d-102">ICorDebugAppDomain2::GetArrayOrPointerType Metodu</span><span class="sxs-lookup"><span data-stu-id="20f7d-102">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>
<span data-ttu-id="20f7d-103">Belirtilen türe veya bir işaretçi veya belirtilen tür referansı dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="20f7d-103">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20f7d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20f7d-104">Syntax</span></span>  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20f7d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20f7d-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="20f7d-106">[in] Temel alınan yerel tür (bir dizi, işaretçi veya başvuru) oluşturulacak belirtir CorElementType numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="20f7d-106">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="20f7d-107">[in] Derecesini (diğer bir deyişle, Boyutlar sayısı) dizisi.</span><span class="sxs-lookup"><span data-stu-id="20f7d-107">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="20f7d-108">Bu değer 0 olmalıdır `elementType` bir işaretçi veya başvuru türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="20f7d-108">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="20f7d-109">[in] İşaretçi Icordebugtype nesneye dizi türünü temsil eder, işaretçi veya başvuru oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="20f7d-109">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="20f7d-110">[out] Adresine bir işaretçi bir `ICorDebugType` oluşturulan dizi, işaretçi türü veya reference temsil eden nesne türü.</span><span class="sxs-lookup"><span data-stu-id="20f7d-110">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20f7d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20f7d-111">Remarks</span></span>  
 <span data-ttu-id="20f7d-112">Değeri *elementType* şunlardan biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="20f7d-112">The value of *elementType* must be one of the following:</span></span>  
  
-   <span data-ttu-id="20f7d-113">ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="20f7d-113">ELEMENT_TYPE_PTR</span></span>  
  
-   <span data-ttu-id="20f7d-114">ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="20f7d-114">ELEMENT_TYPE_BYREF</span></span>  
  
-   <span data-ttu-id="20f7d-115">ELEMENT_TYPE_ARRAY veya ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="20f7d-115">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="20f7d-116">Varsa değerini *elementType* ELEMENT_TYPE_PTR veya ELEMENT_TYPE_BYREF, *nRank* sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20f7d-116">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20f7d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20f7d-117">Requirements</span></span>  
 <span data-ttu-id="20f7d-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20f7d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20f7d-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20f7d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20f7d-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20f7d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20f7d-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20f7d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
