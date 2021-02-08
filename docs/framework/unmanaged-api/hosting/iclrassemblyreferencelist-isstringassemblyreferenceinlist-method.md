---
description: ': ICLRAssemblyReferenceList:: IsStringAssemblyReferenceInList Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 667764337fbda22a526e51575faf049efc4b86ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790041"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="fb7ef-103">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb7ef-103">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>

<span data-ttu-id="fb7ef-104">Sağlanan adın listedeki bir derlemenin adıyla eşleşip eşleşmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="fb7ef-104">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb7ef-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb7ef-105">Syntax</span></span>  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb7ef-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb7ef-106">Parameters</span></span>  

 `pwzAssemblyName`  
 <span data-ttu-id="fb7ef-107">'ndaki Aranacak derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="fb7ef-107">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb7ef-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fb7ef-108">Return Value</span></span>  
  
|<span data-ttu-id="fb7ef-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb7ef-109">HRESULT</span></span>|<span data-ttu-id="fb7ef-110">Description</span><span class="sxs-lookup"><span data-stu-id="fb7ef-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb7ef-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb7ef-111">S_OK</span></span>|<span data-ttu-id="fb7ef-112">Dize listede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fb7ef-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="fb7ef-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="fb7ef-113">S_FALSE</span></span>|<span data-ttu-id="fb7ef-114">Dize listede görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="fb7ef-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="fb7ef-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fb7ef-115">E_FAIL</span></span>|<span data-ttu-id="fb7ef-116">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fb7ef-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fb7ef-117">Bir yöntem E_FAIL döndüğünde, ortak dil çalışma zamanı artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fb7ef-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="fb7ef-118">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fb7ef-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fb7ef-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb7ef-119">Requirements</span></span>  

 <span data-ttu-id="fb7ef-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb7ef-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb7ef-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fb7ef-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb7ef-122">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fb7ef-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb7ef-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb7ef-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb7ef-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb7ef-124">See also</span></span>

- [<span data-ttu-id="fb7ef-125">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb7ef-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="fb7ef-126">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb7ef-126">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="fb7ef-127">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb7ef-127">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="fb7ef-128">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb7ef-128">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
