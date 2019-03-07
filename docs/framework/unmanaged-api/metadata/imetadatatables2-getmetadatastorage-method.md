---
title: IMetaDataTables2::GetMetaDataStorage Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c177a315a76009b7ac82055cba2d0b23821333b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494889"
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="db3ba-102">IMetaDataTables2::GetMetaDataStorage Metodu</span><span class="sxs-lookup"><span data-stu-id="db3ba-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>
<span data-ttu-id="db3ba-103">Boyut ve belirtilen bölümde depolanan meta veriler içeriğini alır.</span><span class="sxs-lookup"><span data-stu-id="db3ba-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db3ba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db3ba-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db3ba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db3ba-105">Parameters</span></span>  
 `ppvMd`  
 <span data-ttu-id="db3ba-106">[out içinde] Bir meta veri bölümü için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db3ba-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="db3ba-107">[out] Meta veri akış boyutu.</span><span class="sxs-lookup"><span data-stu-id="db3ba-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db3ba-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db3ba-108">Requirements</span></span>  
 <span data-ttu-id="db3ba-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db3ba-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db3ba-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="db3ba-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db3ba-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="db3ba-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db3ba-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db3ba-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db3ba-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db3ba-113">See also</span></span>
- [<span data-ttu-id="db3ba-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db3ba-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="db3ba-115">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db3ba-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
