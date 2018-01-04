---
title: IMetaDataTables::GetNextString Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetNextString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2bf16f6debd50729a95a4e887a01c1158b7a937
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="0b14b-102">IMetaDataTables::GetNextString Metodu</span><span class="sxs-lookup"><span data-stu-id="0b14b-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="0b14b-103">Sonraki dizenin dizini geçerli bir tablo sütununda alır.</span><span class="sxs-lookup"><span data-stu-id="0b14b-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b14b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b14b-104">Syntax</span></span>  
  
```  
HRESULT GetNextString (   
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b14b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b14b-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="0b14b-106">[in] Bir dize tablo sütunu dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="0b14b-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="0b14b-107">[out] Sonraki dizenin sütun dizini için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0b14b-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b14b-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b14b-108">Requirements</span></span>  
 <span data-ttu-id="0b14b-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b14b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b14b-110">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0b14b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b14b-111">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0b14b-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b14b-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b14b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b14b-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b14b-113">See Also</span></span>  
 [<span data-ttu-id="0b14b-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b14b-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="0b14b-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b14b-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
