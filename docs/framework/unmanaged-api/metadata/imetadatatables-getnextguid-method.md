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
ms.openlocfilehash: 345c43b5a6e3c185b5e8070e9d6e1c1443673149
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781462"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="5fd12-102">IMetaDataTables::GetNextGuid Metodu</span><span class="sxs-lookup"><span data-stu-id="5fd12-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="5fd12-103">Geçerli bir tablo sütununda sonraki GUID değeri dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="5fd12-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fd12-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fd12-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fd12-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5fd12-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="5fd12-106">[in] Bir GUID tablo sütunu dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="5fd12-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="5fd12-107">[out] Sonraki GUID değeri dizini için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5fd12-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fd12-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5fd12-108">Remarks</span></span>  
 <span data-ttu-id="5fd12-109">Tutarlı sonuçlar döndürmez çünkü bu yöntem kullanımını önermeyiz.</span><span class="sxs-lookup"><span data-stu-id="5fd12-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="5fd12-110">Ortak dil altyapısı (CLI) belgeleri GUID tablosu hakkında daha fazla bilgi için bkz. özellikle "Bölüm II: Meta veri tanımı ve anlamı".</span><span class="sxs-lookup"><span data-stu-id="5fd12-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="5fd12-111">Belgeler çevrimiçi olarak kullanılabilir; bkz: [ECMA C# ve ortak dil altyapısı standartları](https://go.microsoft.com/fwlink/?LinkID=99212) MSDN'de ve [standart ECMA-335 - ortak dil altyapısı (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) Ecma uluslararası Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="5fd12-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fd12-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5fd12-112">Requirements</span></span>  
 <span data-ttu-id="5fd12-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fd12-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fd12-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5fd12-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5fd12-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="5fd12-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5fd12-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fd12-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fd12-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fd12-117">See also</span></span>

- [<span data-ttu-id="5fd12-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5fd12-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="5fd12-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5fd12-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
