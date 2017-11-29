---
title: "CreateAssemblyNameObject İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyNameObject
helpviewer_keywords: CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8281c7944ff96110145a6f5c43a0a0e7da58fdcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="2e2a2-102">CreateAssemblyNameObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="2e2a2-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="2e2a2-103">Bir arabirim işaretçisi alır bir [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) belirtilen ada sahip bir derleme benzersiz kimliğini temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="2e2a2-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e2a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e2a2-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e2a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e2a2-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="2e2a2-106">[out] Döndürülen `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="2e2a2-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="2e2a2-107">[in] Derlemenin oluşturulacağı yeni adını `IAssemblyName` örneği.</span><span class="sxs-lookup"><span data-stu-id="2e2a2-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2e2a2-108">[in] Nesne oluşturucuya geçirmek için işaretler.</span><span class="sxs-lookup"><span data-stu-id="2e2a2-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="2e2a2-109">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="2e2a2-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="2e2a2-110">`pvReserved`bir null başvuru olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e2a2-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e2a2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e2a2-111">Requirements</span></span>  
 <span data-ttu-id="2e2a2-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e2a2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e2a2-113">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2e2a2-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2e2a2-114">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2e2a2-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2e2a2-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e2a2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e2a2-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2e2a2-116">See Also</span></span>  
 [<span data-ttu-id="2e2a2-117">Iassemblyname arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e2a2-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="2e2a2-118">Fusion genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="2e2a2-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
