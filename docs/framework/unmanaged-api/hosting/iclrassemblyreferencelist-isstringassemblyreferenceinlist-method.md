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
ms.openlocfilehash: 91f174cab4986882df795eb531baedfc0dd43962
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615871"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="c2f72-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2f72-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="c2f72-103">Sağlanan adın listedeki bir derlemenin adıyla eşleşip eşleşmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="c2f72-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2f72-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c2f72-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2f72-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2f72-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="c2f72-106">'ndaki Aranacak derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="c2f72-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2f72-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c2f72-107">Return Value</span></span>  
  
|<span data-ttu-id="c2f72-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2f72-108">HRESULT</span></span>|<span data-ttu-id="c2f72-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2f72-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2f72-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2f72-110">S_OK</span></span>|<span data-ttu-id="c2f72-111">Dize listede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c2f72-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="c2f72-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c2f72-112">S_FALSE</span></span>|<span data-ttu-id="c2f72-113">Dize listede görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="c2f72-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="c2f72-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c2f72-114">E_FAIL</span></span>|<span data-ttu-id="c2f72-115">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c2f72-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c2f72-116">Bir yöntem E_FAIL döndüğünde, ortak dil çalışma zamanı artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c2f72-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="c2f72-117">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c2f72-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2f72-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2f72-118">Requirements</span></span>  
 <span data-ttu-id="c2f72-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2f72-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2f72-120">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c2f72-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2f72-121">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c2f72-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2f72-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2f72-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2f72-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2f72-123">See also</span></span>

- [<span data-ttu-id="c2f72-124">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2f72-124">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="c2f72-125">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2f72-125">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="c2f72-126">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2f72-126">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="c2f72-127">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2f72-127">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
