---
title: IMetaDataTables::GetRow Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a02719651d8169c1122f5a46b1b8df39b28612ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197288"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="c8614-102">IMetaDataTables::GetRow Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8614-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="c8614-103">Belirtilen tablo dizini altındaki tabloda belirtilen satır dizinindeki bir satır alır.</span><span class="sxs-lookup"><span data-stu-id="c8614-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8614-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8614-104">Syntax</span></span>  
  
```  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8614-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8614-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="c8614-106">[in] Satır alınır tablosu dizini.</span><span class="sxs-lookup"><span data-stu-id="c8614-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="c8614-107">[in] Alınacak satırın dizini.</span><span class="sxs-lookup"><span data-stu-id="c8614-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="c8614-108">[out] Satır için bir işaretçi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c8614-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8614-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8614-109">Remarks</span></span>  
 <span data-ttu-id="c8614-110">Tutarlı sonuçlar döndürmez çünkü bu yöntem kullanımını önermeyiz.</span><span class="sxs-lookup"><span data-stu-id="c8614-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="c8614-111">Ortak dil altyapısı (CLI) belgeleri GUID tablosu hakkında daha fazla bilgi için bkz. özellikle "Bölüm II: Meta veri tanımı ve anlamı".</span><span class="sxs-lookup"><span data-stu-id="c8614-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="c8614-112">Belgeler çevrimiçi olarak kullanılabilir; bkz: [ECMA C# ve ortak dil altyapısı standartları](https://go.microsoft.com/fwlink/?LinkID=99212) MSDN'de ve [standart ECMA-335 - ortak dil altyapısı (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) Ecma uluslararası Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="c8614-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8614-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8614-113">Requirements</span></span>  
 <span data-ttu-id="c8614-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8614-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8614-115">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c8614-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c8614-116">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="c8614-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="c8614-117">.NET framework sürümleri</span><span class="sxs-lookup"><span data-stu-id="c8614-117">.NET Framework Versions</span></span>**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c8614-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8614-118">See also</span></span>

- [<span data-ttu-id="c8614-119">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8614-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="c8614-120">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8614-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
