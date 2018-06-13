---
title: IMetaDataTables::GetStringHeapSize Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetStringHeapSize method [.NET Framework metadata]
- GetStringHeapSize method [.NET Framework metadata]
ms.assetid: ed8f6335-81f5-4c09-81a9-2a909fc530c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d814a741bc88bb50bfe9ddc3db57635a7266a82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449926"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="fa579-102">IMetaDataTables::GetStringHeapSize Metodu</span><span class="sxs-lookup"><span data-stu-id="fa579-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="fa579-103">Dize yığın bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="fa579-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa579-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa579-104">Syntax</span></span>  
  
```  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa579-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa579-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="fa579-106">[out] Bir işaretçi bayt dizesi yığın boyutu.</span><span class="sxs-lookup"><span data-stu-id="fa579-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa579-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa579-107">Requirements</span></span>  
 <span data-ttu-id="fa579-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa579-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa579-109">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fa579-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fa579-110">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="fa579-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fa579-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa579-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa579-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa579-112">See Also</span></span>  
 [<span data-ttu-id="fa579-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa579-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="fa579-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa579-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
