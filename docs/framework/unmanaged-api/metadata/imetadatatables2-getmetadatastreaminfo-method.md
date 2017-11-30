---
title: IMetaDataTables2::GetMetaDataStreamInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables2.GetMetaDataStreamInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b1631ae8398a8daa910931ff705440a2be0cf21b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="2b847-102">IMetaDataTables2::GetMetaDataStreamInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="2b847-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="2b847-103">Adı, boyutu ve belirtilen dizindeki meta veri akışı içeriğini alır.</span><span class="sxs-lookup"><span data-stu-id="2b847-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b847-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b847-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b847-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b847-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="2b847-106">[in] İstenen meta veri akışın dizini.</span><span class="sxs-lookup"><span data-stu-id="2b847-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="2b847-107">[out] Akış adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2b847-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="2b847-108">[out] Meta veri akışı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2b847-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="2b847-109">[out] Bayt olarak boyutu, `ppv`.</span><span class="sxs-lookup"><span data-stu-id="2b847-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b847-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b847-110">Requirements</span></span>  
 <span data-ttu-id="2b847-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b847-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b847-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2b847-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b847-113">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2b847-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b847-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b847-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b847-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b847-115">See Also</span></span>  
 [<span data-ttu-id="2b847-116">Imetadatatables2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b847-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 [<span data-ttu-id="2b847-117">Imetadatatables arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b847-117">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
