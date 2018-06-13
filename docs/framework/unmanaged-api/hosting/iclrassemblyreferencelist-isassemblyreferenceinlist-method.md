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
ms.openlocfilehash: 0b7eeadd532e5a53c693cc1cde59150777d7edc2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433873"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="b4069-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b4069-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="b4069-103">Sağlanan işaretçi bütünleştirilmiş listesinde başvurduğu olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b4069-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4069-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4069-104">Syntax</span></span>  
  
```  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4069-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b4069-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="b4069-106">[in] Arabirim işaretçisi aranacak derleme.</span><span class="sxs-lookup"><span data-stu-id="b4069-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="b4069-107">Geçerli değerler türünü `IAssemblyName` veya `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="b4069-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4069-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b4069-108">Return Value</span></span>  
  
|<span data-ttu-id="b4069-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b4069-109">HRESULT</span></span>|<span data-ttu-id="b4069-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4069-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b4069-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4069-111">S_OK</span></span>|<span data-ttu-id="b4069-112">Dize listede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b4069-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="b4069-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b4069-113">S_FALSE</span></span>|<span data-ttu-id="b4069-114">Dize, listede görünmez.</span><span class="sxs-lookup"><span data-stu-id="b4069-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="b4069-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b4069-115">E_FAIL</span></span>|<span data-ttu-id="b4069-116">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b4069-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b4069-117">Ortak dil çalışma zamanı, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b4069-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="b4069-118">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b4069-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b4069-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4069-119">Requirements</span></span>  
 <span data-ttu-id="b4069-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4069-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4069-121">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b4069-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4069-122">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b4069-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4069-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4069-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4069-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b4069-124">See Also</span></span>  
 [<span data-ttu-id="b4069-125">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4069-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="b4069-126">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4069-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="b4069-127">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4069-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="b4069-128">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4069-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
