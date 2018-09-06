---
title: IMetaDataTables::GetNextGuid Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3273f89d61314db2ae36c572f2ca520f28e63e3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802858"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="a591b-102">IMetaDataTables::GetNextGuid Metodu</span><span class="sxs-lookup"><span data-stu-id="a591b-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="a591b-103">Geçerli bir tablo sütununda sonraki GUID değeri dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="a591b-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a591b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a591b-104">Syntax</span></span>  
  
```  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a591b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a591b-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="a591b-106">[in] Bir GUID tablo sütunu dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="a591b-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="a591b-107">[out] Sonraki GUID değeri dizini için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a591b-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a591b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a591b-108">Remarks</span></span>  
 <span data-ttu-id="a591b-109">Tutarlı sonuçlar döndürmez çünkü bu yöntem kullanımını önermeyiz.</span><span class="sxs-lookup"><span data-stu-id="a591b-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="a591b-110">GUID tablosu hakkında daha fazla bilgi için özellikle "Bölüm II: meta veri tanımı ve semantiği" ortak dil altyapısı (CLI) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="a591b-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="a591b-111">Belgeler çevrimiçi olarak kullanılabilir; bkz: [ECMA C# ve ortak dil altyapısı standartları](https://go.microsoft.com/fwlink/?LinkID=99212) MSDN'de ve [standart ECMA-335 - ortak dil altyapısı (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) Ecma uluslararası Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="a591b-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a591b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a591b-112">Requirements</span></span>  
 <span data-ttu-id="a591b-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a591b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a591b-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a591b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a591b-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılan</span><span class="sxs-lookup"><span data-stu-id="a591b-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a591b-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a591b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a591b-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a591b-117">See Also</span></span>  
 [<span data-ttu-id="a591b-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a591b-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="a591b-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a591b-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
