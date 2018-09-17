---
title: IMetaDataTables::GetGuid Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f589225dde1ba2aabc4ca32542339a771c3287d4
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45742949"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="dcb51-102">IMetaDataTables::GetGuid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dcb51-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="dcb51-103">Belirtilen dizindeki satırdaki bir GUID alır.</span><span class="sxs-lookup"><span data-stu-id="dcb51-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcb51-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dcb51-104">Syntax</span></span>  
  
```  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcb51-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dcb51-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="dcb51-106">[in] Satır GUID alınacağı dizin.</span><span class="sxs-lookup"><span data-stu-id="dcb51-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="dcb51-107">[out] GUID işaretçisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dcb51-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcb51-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dcb51-108">Remarks</span></span>  
 <span data-ttu-id="dcb51-109">Tutarlı sonuçlar döndürmez çünkü bu yöntem kullanımını önermeyiz.</span><span class="sxs-lookup"><span data-stu-id="dcb51-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="dcb51-110">GUID tablosu hakkında daha fazla bilgi için özellikle "Bölüm II: meta veri tanımı ve semantiği" ortak dil altyapısı (CLI) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="dcb51-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="dcb51-111">Belgeler çevrimiçi olarak kullanılabilir; bkz: [ECMA C# ve ortak dil altyapısı standartları](https://go.microsoft.com/fwlink/?LinkID=99212) MSDN'de ve [standart ECMA-335 - ortak dil altyapısı (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) Ecma uluslararası Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="dcb51-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcb51-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dcb51-112">Requirements</span></span>  
 <span data-ttu-id="dcb51-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcb51-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcb51-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dcb51-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dcb51-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılan</span><span class="sxs-lookup"><span data-stu-id="dcb51-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dcb51-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcb51-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb51-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dcb51-117">See Also</span></span>  
 [<span data-ttu-id="dcb51-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dcb51-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="dcb51-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dcb51-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
