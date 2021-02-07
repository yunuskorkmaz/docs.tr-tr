---
description: ': ICLRAssemblyReferenceList:: IsAssemblyReferenceInList yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ce90423715d6cbe07c1112cb2136c11fd58c982a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716776"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="65006-103">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65006-103">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>

<span data-ttu-id="65006-104">Sağlanan işaretçinin listedeki bir derlemeyi içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="65006-104">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65006-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65006-105">Syntax</span></span>  
  
```cpp  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65006-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65006-106">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="65006-107">'ndaki Aranacak derlemeye yönelik bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="65006-107">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="65006-108">Geçerli değerler `IAssemblyName` veya türündedir `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="65006-108">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65006-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="65006-109">Return Value</span></span>  
  
|<span data-ttu-id="65006-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="65006-110">HRESULT</span></span>|<span data-ttu-id="65006-111">Description</span><span class="sxs-lookup"><span data-stu-id="65006-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65006-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="65006-112">S_OK</span></span>|<span data-ttu-id="65006-113">Dize listede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="65006-113">The string appears in the list.</span></span>|  
|<span data-ttu-id="65006-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="65006-114">S_FALSE</span></span>|<span data-ttu-id="65006-115">Dize listede görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="65006-115">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="65006-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="65006-116">E_FAIL</span></span>|<span data-ttu-id="65006-117">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="65006-117">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="65006-118">Bir yöntem E_FAIL döndüğünde, ortak dil çalışma zamanı artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="65006-118">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="65006-119">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="65006-119">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65006-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65006-120">Requirements</span></span>  

 <span data-ttu-id="65006-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65006-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65006-122">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="65006-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65006-123">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="65006-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65006-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65006-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65006-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65006-125">See also</span></span>

- [<span data-ttu-id="65006-126">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65006-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="65006-127">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65006-127">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="65006-128">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65006-128">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="65006-129">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65006-129">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
