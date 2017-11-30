---
title: ICorDebugAppDomain2::GetFunctionPointerType Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain2.GetFunctionPointerType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 85c07ec6177621b571a376ad58a386e8ed31ea63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="aecb8-102">ICorDebugAppDomain2::GetFunctionPointerType Metodu</span><span class="sxs-lookup"><span data-stu-id="aecb8-102">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>
<span data-ttu-id="aecb8-103">Bir işaretçi belirli bir imzaya sahip bir işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="aecb8-103">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aecb8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aecb8-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aecb8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aecb8-105">Parameters</span></span>  
 `nTypeArgs`  
 <span data-ttu-id="aecb8-106">[in] İşlevi için tür bağımsız değişkenleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="aecb8-106">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="aecb8-107">[in] Her biri bir tür bağımsız değişkeni işlevinin temsil eden bir Icordebugtype bir nesneye işaret etmiyor dizisi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="aecb8-107">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="aecb8-108">Dönüş türü olan ilk öğedir; diğer öğelerin her biri bir parametre türüdür.</span><span class="sxs-lookup"><span data-stu-id="aecb8-108">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="aecb8-109">[out] Adresine bir işaretçi bir `ICorDebugType` işaretçinin işleve temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="aecb8-109">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aecb8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aecb8-110">Requirements</span></span>  
 <span data-ttu-id="aecb8-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aecb8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aecb8-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aecb8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aecb8-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aecb8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aecb8-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aecb8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
