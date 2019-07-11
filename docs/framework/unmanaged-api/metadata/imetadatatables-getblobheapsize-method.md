---
title: IMetaDataTables::GetBlobHeapSize Yöntemi
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
ms.openlocfilehash: b9a73df0b73eb5043103479b7452fedc84b02819
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781551"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="19a92-102">IMetaDataTables::GetBlobHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19a92-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="19a92-103">İkili büyük nesne (BLOB) yığını bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="19a92-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19a92-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19a92-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="19a92-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="19a92-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="19a92-106">[out] BLOB yığın bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="19a92-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19a92-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19a92-107">Requirements</span></span>  
 <span data-ttu-id="19a92-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19a92-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19a92-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="19a92-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19a92-110">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="19a92-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="19a92-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19a92-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19a92-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19a92-112">See also</span></span>

- [<span data-ttu-id="19a92-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19a92-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="19a92-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19a92-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
