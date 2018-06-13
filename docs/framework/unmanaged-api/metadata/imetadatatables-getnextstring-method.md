---
title: IMetaDataTables::GetNextString Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eea43e5eaa037a3b70f482b0602d8d8d3d594f75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449855"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="286c0-102">IMetaDataTables::GetNextString Metodu</span><span class="sxs-lookup"><span data-stu-id="286c0-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="286c0-103">Sonraki dizenin dizini geçerli bir tablo sütununda alır.</span><span class="sxs-lookup"><span data-stu-id="286c0-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="286c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="286c0-104">Syntax</span></span>  
  
```  
HRESULT GetNextString (   
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="286c0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="286c0-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="286c0-106">[in] Bir dize tablo sütunu dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="286c0-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="286c0-107">[out] Sonraki dizenin sütun dizini için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="286c0-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="286c0-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="286c0-108">Requirements</span></span>  
 <span data-ttu-id="286c0-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="286c0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="286c0-110">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="286c0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="286c0-111">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="286c0-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="286c0-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="286c0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="286c0-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="286c0-113">See Also</span></span>  
 [<span data-ttu-id="286c0-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="286c0-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="286c0-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="286c0-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
