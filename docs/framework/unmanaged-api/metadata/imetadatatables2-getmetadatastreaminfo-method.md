---
title: IMetaDataTables2::GetMetaDataStreamInfo Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57fa18df1baece984a745725dba614e8c4bb1450
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471462"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="ad2bb-102">IMetaDataTables2::GetMetaDataStreamInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="ad2bb-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="ad2bb-103">Adı, boyutu ve belirtilen dizine metaveri akışı içeriğini alır.</span><span class="sxs-lookup"><span data-stu-id="ad2bb-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad2bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad2bb-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad2bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad2bb-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="ad2bb-106">[in] İstenen meta veri akışın dizini.</span><span class="sxs-lookup"><span data-stu-id="ad2bb-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="ad2bb-107">[out] Akış adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ad2bb-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="ad2bb-108">[out] Meta veri akışı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ad2bb-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="ad2bb-109">[out] Bayt cinsinden boyutu, `ppv`.</span><span class="sxs-lookup"><span data-stu-id="ad2bb-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad2bb-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad2bb-110">Requirements</span></span>  
 <span data-ttu-id="ad2bb-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad2bb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad2bb-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ad2bb-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad2bb-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="ad2bb-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ad2bb-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad2bb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad2bb-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad2bb-115">See also</span></span>
- [<span data-ttu-id="ad2bb-116">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad2bb-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="ad2bb-117">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad2bb-117">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
