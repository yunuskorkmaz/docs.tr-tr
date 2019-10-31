---
title: ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type:
- apiref
ms.openlocfilehash: 4dc91723f009d46f9c57b1c99aa66ba7a1b127e4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126642"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="9608d-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9608d-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="9608d-103">Sağlanan adın listedeki bir derlemenin adıyla eşleşip eşleşmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="9608d-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9608d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9608d-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9608d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9608d-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="9608d-106">'ndaki Aranacak derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="9608d-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9608d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9608d-107">Return Value</span></span>  
  
|<span data-ttu-id="9608d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9608d-108">HRESULT</span></span>|<span data-ttu-id="9608d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9608d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9608d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9608d-110">S_OK</span></span>|<span data-ttu-id="9608d-111">Dize listede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9608d-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="9608d-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9608d-112">S_FALSE</span></span>|<span data-ttu-id="9608d-113">Dize listede görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="9608d-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="9608d-114">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="9608d-114">E_FAIL</span></span>|<span data-ttu-id="9608d-115">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9608d-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9608d-116">Bir yöntem E_FAıL döndüğünde, ortak dil çalışma zamanı artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9608d-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="9608d-117">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9608d-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9608d-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9608d-118">Requirements</span></span>  
 <span data-ttu-id="9608d-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9608d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9608d-120">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9608d-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9608d-121">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9608d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9608d-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9608d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9608d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9608d-123">See also</span></span>

- [<span data-ttu-id="9608d-124">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9608d-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="9608d-125">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9608d-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="9608d-126">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9608d-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="9608d-127">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9608d-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
