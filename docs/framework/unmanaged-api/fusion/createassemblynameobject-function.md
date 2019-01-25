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
ms.openlocfilehash: 1412231b53763ce8e6c2400497396d2f178d8e7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666299"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="2e6e7-102">CreateAssemblyNameObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="2e6e7-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="2e6e7-103">Bir arabirim işaretçisi alır bir [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) belirtilen ada sahip derlemeyi benzersiz kimliğini temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="2e6e7-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e6e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e6e7-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e6e7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e6e7-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="2e6e7-106">[out] Döndürülen `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="2e6e7-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="2e6e7-107">[in] Derlemenin oluşturulacağı yeni adı `IAssemblyName` örneği.</span><span class="sxs-lookup"><span data-stu-id="2e6e7-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2e6e7-108">[in] Nesne oluşturucuya geçirilecek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="2e6e7-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="2e6e7-109">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="2e6e7-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="2e6e7-110">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2e6e7-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e6e7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e6e7-111">Requirements</span></span>  
 <span data-ttu-id="2e6e7-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e6e7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e6e7-113">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2e6e7-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2e6e7-114">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2e6e7-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2e6e7-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e6e7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e6e7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e6e7-116">See also</span></span>
- [<span data-ttu-id="2e6e7-117">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e6e7-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="2e6e7-118">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2e6e7-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
