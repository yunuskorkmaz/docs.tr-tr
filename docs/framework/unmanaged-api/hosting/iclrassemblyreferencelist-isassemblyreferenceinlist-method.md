---
title: ICLRAssemblyReferenceList::IsAssemblyReferenceInList Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type:
- apiref
ms.openlocfilehash: 4e75b8553ff33946654a6a3b6184f98049c6a6cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126677"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="80c7f-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80c7f-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="80c7f-103">Sağlanan işaretçinin listedeki bir derlemeyi içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="80c7f-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80c7f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80c7f-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80c7f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80c7f-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="80c7f-106">'ndaki Aranacak derlemeye yönelik bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="80c7f-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="80c7f-107">Geçerli değerler `IAssemblyName` veya `IReferenceIdentity`türündedir.</span><span class="sxs-lookup"><span data-stu-id="80c7f-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80c7f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="80c7f-108">Return Value</span></span>  
  
|<span data-ttu-id="80c7f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="80c7f-109">HRESULT</span></span>|<span data-ttu-id="80c7f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80c7f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80c7f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="80c7f-111">S_OK</span></span>|<span data-ttu-id="80c7f-112">Dize listede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="80c7f-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="80c7f-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="80c7f-113">S_FALSE</span></span>|<span data-ttu-id="80c7f-114">Dize listede görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="80c7f-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="80c7f-115">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="80c7f-115">E_FAIL</span></span>|<span data-ttu-id="80c7f-116">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="80c7f-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="80c7f-117">Bir yöntem E_FAıL döndüğünde, ortak dil çalışma zamanı artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="80c7f-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="80c7f-118">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="80c7f-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80c7f-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80c7f-119">Requirements</span></span>  
 <span data-ttu-id="80c7f-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80c7f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80c7f-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="80c7f-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80c7f-122">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="80c7f-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80c7f-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80c7f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80c7f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80c7f-124">See also</span></span>

- [<span data-ttu-id="80c7f-125">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80c7f-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="80c7f-126">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80c7f-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="80c7f-127">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80c7f-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="80c7f-128">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80c7f-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
