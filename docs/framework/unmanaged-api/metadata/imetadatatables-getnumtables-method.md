---
title: IMetaDataTables::GetNumTables Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNumTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNumTables
helpviewer_keywords:
- GetNumTables method [.NET Framework metadata]
- IMetaDataTables::GetNumTables method [.NET Framework metadata]
ms.assetid: 8196f2a3-bbf2-45d3-a6cd-74502c356644
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9ffd9ab9ddb95945744ecf210d0ae1d9d9812ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125833"
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="c5d96-102">IMetaDataTables::GetNumTables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5d96-102">IMetaDataTables::GetNumTables Method</span></span>
<span data-ttu-id="c5d96-103">Tablo sayısı geçerli kapsamda alır `IMetaDataTables` örneği.</span><span class="sxs-lookup"><span data-stu-id="c5d96-103">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5d96-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5d96-104">Syntax</span></span>  
  
```  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5d96-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5d96-105">Parameters</span></span>  
 `pcTables`  
 <span data-ttu-id="c5d96-106">[out] Geçerli örnek kapsamdaki tablo sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c5d96-106">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5d96-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5d96-107">Requirements</span></span>  
 <span data-ttu-id="c5d96-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5d96-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5d96-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c5d96-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5d96-110">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="c5d96-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c5d96-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5d96-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5d96-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5d96-112">See also</span></span>

- [<span data-ttu-id="c5d96-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5d96-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="c5d96-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5d96-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
