---
title: IMetaDataTables::GetGuid Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetGuid
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58dbcb7ebf56f126d89a42a1f5df6247266cb38c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="7a21e-102">IMetaDataTables::GetGuid Metodu</span><span class="sxs-lookup"><span data-stu-id="7a21e-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="7a21e-103">Belirtilen dizindeki satırdan bir GUID alır.</span><span class="sxs-lookup"><span data-stu-id="7a21e-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a21e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a21e-104">Syntax</span></span>  
  
```  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a21e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a21e-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="7a21e-106">[in] GUID alınacağı satır dizini.</span><span class="sxs-lookup"><span data-stu-id="7a21e-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="7a21e-107">[out] GUID için bir işaretçi bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7a21e-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a21e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a21e-108">Remarks</span></span>  
 <span data-ttu-id="7a21e-109">Tutarlı sonuçlar döndürmüyor olduğundan, bu yöntemin kullanılması önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="7a21e-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="7a21e-110">GUID tablosu hakkında daha fazla bilgi için özellikle "Bölüm II: meta veri tanım ve semantiği" ortak dil altyapısı (CLI) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="7a21e-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="7a21e-111">Belge çevrimiçi kullanılabilir; bkz: [ECMA C# ve ortak dil altyapısı standartları](http://go.microsoft.com/fwlink/?LinkID=99212) MSDN'de ve [standart ECMA-335 - ortak dil altyapısı (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) Ecma uluslararası Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="7a21e-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a21e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a21e-112">Requirements</span></span>  
 <span data-ttu-id="7a21e-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a21e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a21e-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7a21e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7a21e-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="7a21e-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7a21e-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a21e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a21e-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a21e-117">See Also</span></span>  
 [<span data-ttu-id="7a21e-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a21e-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="7a21e-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a21e-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
