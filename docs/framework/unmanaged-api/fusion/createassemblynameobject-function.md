---
title: CreateAssemblyNameObject İşlevi
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5433c49db8e507c6026ab0e87040dd5634ad0808
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430444"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="40f44-102">CreateAssemblyNameObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="40f44-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="40f44-103">Bir arabirim işaretçisi alır bir [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) belirtilen ada sahip bir derleme benzersiz kimliğini temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="40f44-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40f44-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40f44-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40f44-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40f44-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="40f44-106">[out] Döndürülen `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="40f44-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="40f44-107">[in] Derlemenin oluşturulacağı yeni adını `IAssemblyName` örneği.</span><span class="sxs-lookup"><span data-stu-id="40f44-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="40f44-108">[in] Nesne oluşturucuya geçirmek için işaretler.</span><span class="sxs-lookup"><span data-stu-id="40f44-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="40f44-109">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="40f44-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="40f44-110">`pvReserved` bir null başvuru olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="40f44-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40f44-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40f44-111">Requirements</span></span>  
 <span data-ttu-id="40f44-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40f44-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40f44-113">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="40f44-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="40f44-114">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="40f44-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="40f44-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40f44-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40f44-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40f44-116">See Also</span></span>  
 [<span data-ttu-id="40f44-117">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40f44-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="40f44-118">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="40f44-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
