---
title: IMetaDataTables::GetStringHeapSize Yöntemi
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
ms.openlocfilehash: b842fb4d0853f473ae8e237a42e800cf0af8dc11
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781383"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="1609a-102">IMetaDataTables::GetStringHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1609a-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="1609a-103">Dize yığın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="1609a-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1609a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1609a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1609a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1609a-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="1609a-106">[out] Bayt cinsinden dize yığın boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1609a-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1609a-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1609a-107">Requirements</span></span>  
 <span data-ttu-id="1609a-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1609a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1609a-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1609a-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1609a-110">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="1609a-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1609a-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1609a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1609a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1609a-112">See also</span></span>

- [<span data-ttu-id="1609a-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1609a-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="1609a-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1609a-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
