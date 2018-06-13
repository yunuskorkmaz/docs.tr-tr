---
title: IMetaDataTables::GetUserStringHeapSize Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a217a835e258052ace5b59a70cbc0fa31691d78e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452852"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="e3653-102">IMetaDataTables::GetUserStringHeapSize Metodu</span><span class="sxs-lookup"><span data-stu-id="e3653-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="e3653-103">Kullanıcı dize yığın bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="e3653-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3653-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3653-104">Syntax</span></span>  
  
```  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3653-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e3653-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="e3653-106">[out] Bir işaretçi kullanıcı dize yığın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="e3653-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3653-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3653-107">Requirements</span></span>  
 <span data-ttu-id="e3653-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3653-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3653-109">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e3653-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3653-110">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e3653-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e3653-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3653-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3653-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3653-112">See Also</span></span>  
 [<span data-ttu-id="e3653-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3653-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="e3653-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3653-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
