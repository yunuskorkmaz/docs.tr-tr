---
title: IMetaDataTables::GetNextString Yöntemi
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
ms.openlocfilehash: 3c2008556ebf1b1961aef7dc0f24fd0a3161d06e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781447"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="640d9-102">IMetaDataTables::GetNextString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="640d9-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="640d9-103">Geçerli bir tablo sütununda sonraki dize dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="640d9-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="640d9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="640d9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (   
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="640d9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="640d9-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="640d9-106">[in] Dize tablosu sütunu dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="640d9-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="640d9-107">[out] Dizin sütunu sonraki dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="640d9-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="640d9-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="640d9-108">Requirements</span></span>  
 <span data-ttu-id="640d9-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="640d9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="640d9-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="640d9-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="640d9-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="640d9-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="640d9-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="640d9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="640d9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="640d9-113">See also</span></span>

- [<span data-ttu-id="640d9-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="640d9-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="640d9-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="640d9-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
