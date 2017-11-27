---
title: ICorDebugAssembly::GetName Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d54139f8d7562f7f1ceb6e704731cd890a5f99df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="ffe9e-102">ICorDebugAssembly::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="ffe9e-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="ffe9e-103">Derlemenin adını alır bu `ICorDebugAssembly` örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ffe9e-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffe9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ffe9e-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ffe9e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ffe9e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ffe9e-106">[in] Boyutunu `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="ffe9e-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ffe9e-107">[out] Gerçek adının uzunluğu belirten bir tamsayı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ffe9e-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="ffe9e-108">[out] Adını depolar bir dizi.</span><span class="sxs-lookup"><span data-stu-id="ffe9e-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffe9e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ffe9e-109">Remarks</span></span>  
 <span data-ttu-id="ffe9e-110">`GetName` Yöntemi derleme tam yolunu ve dosya adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="ffe9e-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffe9e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ffe9e-111">Requirements</span></span>  
 <span data-ttu-id="ffe9e-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffe9e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffe9e-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ffe9e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffe9e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffe9e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffe9e-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffe9e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
