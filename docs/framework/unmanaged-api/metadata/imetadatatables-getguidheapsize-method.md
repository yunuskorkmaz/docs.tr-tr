---
title: IMetaDataTables::GetGuidHeapSize Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97d196769b549022ce498958fc34cf08df442d0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447096"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="782dc-102">IMetaDataTables::GetGuidHeapSize Metodu</span><span class="sxs-lookup"><span data-stu-id="782dc-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="782dc-103">GUID yığın bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="782dc-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="782dc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="782dc-104">Syntax</span></span>  
  
```  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="782dc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="782dc-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="782dc-106">[out] Bir işaretçi GUID yığın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="782dc-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="782dc-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="782dc-107">Requirements</span></span>  
 <span data-ttu-id="782dc-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="782dc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="782dc-109">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="782dc-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="782dc-110">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="782dc-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="782dc-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="782dc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="782dc-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="782dc-112">See Also</span></span>  
 [<span data-ttu-id="782dc-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="782dc-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="782dc-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="782dc-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
