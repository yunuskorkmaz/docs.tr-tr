---
title: IMetaDataTables::GetBlobHeapSize Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlobHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlobHeapSize
helpviewer_keywords:
- GetBlobHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetBlobHeapSize method [.NET Framework metadata]
ms.assetid: 6330a9ee-8cd5-4299-86f1-b4de2c701a0d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 787ea506c6698925473175cf7fdac340c0c2eca8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447286"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="4b154-102">IMetaDataTables::GetBlobHeapSize Metodu</span><span class="sxs-lookup"><span data-stu-id="4b154-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="4b154-103">İkili büyük nesne (BLOB) yığın bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="4b154-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b154-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b154-104">Syntax</span></span>  
  
```  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b154-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b154-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="4b154-106">[out] Bir işaretçi BLOB yığın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="4b154-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b154-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b154-107">Requirements</span></span>  
 <span data-ttu-id="4b154-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b154-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b154-109">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4b154-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4b154-110">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4b154-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4b154-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b154-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b154-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b154-112">See Also</span></span>  
 [<span data-ttu-id="4b154-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b154-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="4b154-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b154-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
