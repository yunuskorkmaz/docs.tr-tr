---
title: IMetaDataTables::GetGuid Metodu
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
ms.openlocfilehash: 1075643bbd17765bf33a26038fc6beaf32d0aebb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781500"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="7d6d2-102">IMetaDataTables::GetGuid Metodu</span><span class="sxs-lookup"><span data-stu-id="7d6d2-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="7d6d2-103">Belirtilen dizindeki satırdaki bir GUID alır.</span><span class="sxs-lookup"><span data-stu-id="7d6d2-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d6d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d6d2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d6d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d6d2-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="7d6d2-106">[in] Satır GUID alınacağı dizin.</span><span class="sxs-lookup"><span data-stu-id="7d6d2-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="7d6d2-107">[out] GUID işaretçisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7d6d2-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d6d2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d6d2-108">Remarks</span></span>  
 <span data-ttu-id="7d6d2-109">Tutarlı sonuçlar döndürmez çünkü bu yöntem kullanımını önermeyiz.</span><span class="sxs-lookup"><span data-stu-id="7d6d2-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="7d6d2-110">Ortak dil altyapısı (CLI) belgeleri GUID tablosu hakkında daha fazla bilgi için bkz. özellikle "Bölüm II: Meta veri tanımı ve anlamı".</span><span class="sxs-lookup"><span data-stu-id="7d6d2-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="7d6d2-111">Belgeler çevrimiçi olarak kullanılabilir; bkz: [ECMA C# ve ortak dil altyapısı standartları](https://go.microsoft.com/fwlink/?LinkID=99212) MSDN'de ve [standart ECMA-335 - ortak dil altyapısı (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) Ecma uluslararası Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="7d6d2-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d6d2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d6d2-112">Requirements</span></span>  
 <span data-ttu-id="7d6d2-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d6d2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d6d2-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7d6d2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7d6d2-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="7d6d2-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7d6d2-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d6d2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d6d2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d6d2-117">See also</span></span>

- [<span data-ttu-id="7d6d2-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d6d2-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="7d6d2-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d6d2-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
