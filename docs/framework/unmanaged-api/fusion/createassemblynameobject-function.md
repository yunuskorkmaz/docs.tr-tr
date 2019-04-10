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
ms.openlocfilehash: cd8609bedcea28c1cb8559d378b5e171f3ad568e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225007"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="60ec9-102">CreateAssemblyNameObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="60ec9-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="60ec9-103">Bir arabirim işaretçisi alır bir [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) belirtilen ada sahip derlemeyi benzersiz kimliğini temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="60ec9-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60ec9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60ec9-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="60ec9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60ec9-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="60ec9-106">[out] Döndürülen `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="60ec9-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="60ec9-107">[in] Derlemenin oluşturulacağı yeni adı `IAssemblyName` örneği.</span><span class="sxs-lookup"><span data-stu-id="60ec9-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="60ec9-108">[in] Nesne oluşturucuya geçirilecek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="60ec9-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="60ec9-109">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="60ec9-109">[in] Reserved for future extensibility.</span></span> `pvReserved` <span data-ttu-id="60ec9-110">null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60ec9-110">must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60ec9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60ec9-111">Requirements</span></span>  
 <span data-ttu-id="60ec9-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60ec9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60ec9-113">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="60ec9-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="60ec9-114">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="60ec9-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="60ec9-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="60ec9-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="60ec9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60ec9-116">See also</span></span>

- [<span data-ttu-id="60ec9-117">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60ec9-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="60ec9-118">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="60ec9-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
