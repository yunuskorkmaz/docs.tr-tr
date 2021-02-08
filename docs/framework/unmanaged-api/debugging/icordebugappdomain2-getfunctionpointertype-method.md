---
description: ': ICorDebugAppDomain2:: GetFunctionPointerType Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugAppDomain2::GetFunctionPointerType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetFunctionPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type:
- apiref
ms.openlocfilehash: 2b9e10295df40b8e7db82e489fe8a6d28214ff38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772399"
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="f6a66-103">ICorDebugAppDomain2::GetFunctionPointerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6a66-103">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>

<span data-ttu-id="f6a66-104">Belirli bir imzaya sahip bir işleve yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="f6a66-104">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6a66-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6a66-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6a66-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f6a66-106">Parameters</span></span>  

 `nTypeArgs`  
 <span data-ttu-id="f6a66-107">'ndaki İşlevin tür bağımsız değişkenlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="f6a66-107">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="f6a66-108">'ndaki Her biri işlevin tür bağımsız değişkenini temsil eden bir ICorDebugType nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="f6a66-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="f6a66-109">İlk öğe dönüş türüdür; diğer öğelerin her biri bir parametre türüdür.</span><span class="sxs-lookup"><span data-stu-id="f6a66-109">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="f6a66-110">dışı `ICorDebugType` İşlevin işaretçisini temsil eden nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f6a66-110">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6a66-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6a66-111">Requirements</span></span>  

 <span data-ttu-id="f6a66-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6a66-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6a66-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f6a66-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6a66-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f6a66-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6a66-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6a66-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
