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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6aeda4901551b7e79becff132e44382ed11b0d31
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773345"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="d1982-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1982-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="d1982-103">Sağlanan işaretçi listesinde bir derlemeye başvuran olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d1982-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1982-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1982-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1982-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1982-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="d1982-106">[in] Derleme Aranmak üzere bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d1982-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="d1982-107">Geçerli değerler türünü `IAssemblyName` veya `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="d1982-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1982-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d1982-108">Return Value</span></span>  
  
|<span data-ttu-id="d1982-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1982-109">HRESULT</span></span>|<span data-ttu-id="d1982-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1982-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1982-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1982-111">S_OK</span></span>|<span data-ttu-id="d1982-112">Dize listesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="d1982-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="d1982-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d1982-113">S_FALSE</span></span>|<span data-ttu-id="d1982-114">Dize, listede görünmez.</span><span class="sxs-lookup"><span data-stu-id="d1982-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="d1982-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d1982-115">E_FAIL</span></span>|<span data-ttu-id="d1982-116">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d1982-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d1982-117">Ortak dil çalışma zamanı, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d1982-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="d1982-118">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d1982-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d1982-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1982-119">Requirements</span></span>  
 <span data-ttu-id="d1982-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1982-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1982-121">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d1982-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1982-122">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d1982-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1982-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1982-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1982-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1982-124">See also</span></span>

- [<span data-ttu-id="d1982-125">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1982-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="d1982-126">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1982-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="d1982-127">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1982-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="d1982-128">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1982-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
