---
title: ICorDebugAppDomain2::GetArrayOrPointerType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cc38ef23a8b802d674a7a6dc4807371e432f73d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593510"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="7f0a2-102">ICorDebugAppDomain2::GetArrayOrPointerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f0a2-102">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>
<span data-ttu-id="7f0a2-103">Belirtilen tür veya işaretçi veya başvuru belirtilen türe dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="7f0a2-103">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f0a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f0a2-104">Syntax</span></span>  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f0a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f0a2-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="7f0a2-106">[in] Temel alınan yerel tür (bir dizi, işaretçi veya başvuru) oluşturulacak belirtir CorElementType sabit listesi değeri.</span><span class="sxs-lookup"><span data-stu-id="7f0a2-106">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="7f0a2-107">[in] Boyut (diğer bir deyişle, boyut sayısı) dizisi.</span><span class="sxs-lookup"><span data-stu-id="7f0a2-107">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="7f0a2-108">Bu değer, 0 olmalıdır `elementType` bir işaretçi veya başvuru türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f0a2-108">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="7f0a2-109">[in] Bir dizi türünü temsil eden bir Icordebugtype nesne işaretçisi, işaretçi veya başvuru oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="7f0a2-109">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="7f0a2-110">[out] Adresine bir işaretçi bir `ICorDebugType` oluşturulmuş dizi, işaretçi türü veya başvuru temsil eden bir nesne türü.</span><span class="sxs-lookup"><span data-stu-id="7f0a2-110">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f0a2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f0a2-111">Remarks</span></span>  
 <span data-ttu-id="7f0a2-112">Değerini *elementType* aşağıdakilerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="7f0a2-112">The value of *elementType* must be one of the following:</span></span>  
  
- <span data-ttu-id="7f0a2-113">ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="7f0a2-113">ELEMENT_TYPE_PTR</span></span>  
  
- <span data-ttu-id="7f0a2-114">ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="7f0a2-114">ELEMENT_TYPE_BYREF</span></span>  
  
- <span data-ttu-id="7f0a2-115">ELEMENT_TYPE_ARRAY veya ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="7f0a2-115">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="7f0a2-116">Varsa değerini *elementType* ELEMENT_TYPE_PTR veya ELEMENT_TYPE_BYREF, *nRank* sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f0a2-116">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f0a2-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f0a2-117">Requirements</span></span>  
 <span data-ttu-id="7f0a2-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f0a2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f0a2-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f0a2-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f0a2-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f0a2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f0a2-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f0a2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
