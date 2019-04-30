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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779818"
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="0b540-102">IMetaDataTables::GetNumTables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b540-102">IMetaDataTables::GetNumTables Method</span></span>
<span data-ttu-id="0b540-103">Tablo sayısı geçerli kapsamda alır `IMetaDataTables` örneği.</span><span class="sxs-lookup"><span data-stu-id="0b540-103">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b540-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b540-104">Syntax</span></span>  
  
```  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b540-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b540-105">Parameters</span></span>  
 `pcTables`  
 <span data-ttu-id="0b540-106">[out] Geçerli örnek kapsamdaki tablo sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0b540-106">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b540-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b540-107">Requirements</span></span>  
 <span data-ttu-id="0b540-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b540-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b540-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0b540-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b540-110">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="0b540-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b540-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b540-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b540-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b540-112">See also</span></span>

- [<span data-ttu-id="0b540-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b540-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="0b540-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b540-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
