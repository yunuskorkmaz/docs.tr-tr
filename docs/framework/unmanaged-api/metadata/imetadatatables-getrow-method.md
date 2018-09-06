---
title: IMetaDataTables::GetRow Metodu
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
ms.openlocfilehash: d24dbcbdd8b0ed0736f7b59564cf72dffaa5a8f8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745963"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="94309-102">IMetaDataTables::GetRow Metodu</span><span class="sxs-lookup"><span data-stu-id="94309-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="94309-103">Belirtilen tablo dizini altındaki tabloda belirtilen satır dizinindeki bir satır alır.</span><span class="sxs-lookup"><span data-stu-id="94309-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94309-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94309-104">Syntax</span></span>  
  
```  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94309-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94309-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="94309-106">[in] Satır alınır tablosu dizini.</span><span class="sxs-lookup"><span data-stu-id="94309-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="94309-107">[in] Alınacak satırın dizini.</span><span class="sxs-lookup"><span data-stu-id="94309-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="94309-108">[out] Satır için bir işaretçi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="94309-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94309-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94309-109">Remarks</span></span>  
 <span data-ttu-id="94309-110">Tutarlı sonuçlar döndürmez çünkü bu yöntem kullanımını önermeyiz.</span><span class="sxs-lookup"><span data-stu-id="94309-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="94309-111">GUID tablosu hakkında daha fazla bilgi için özellikle "Bölüm II: meta veri tanımı ve semantiği" ortak dil altyapısı (CLI) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="94309-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="94309-112">Belgeler çevrimiçi olarak kullanılabilir; bkz: [ECMA C# ve ortak dil altyapısı standartları](https://go.microsoft.com/fwlink/?LinkID=99212) MSDN'de ve [standart ECMA-335 - ortak dil altyapısı (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) Ecma uluslararası Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="94309-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94309-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94309-113">Requirements</span></span>  
 <span data-ttu-id="94309-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94309-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94309-115">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="94309-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="94309-116">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılan</span><span class="sxs-lookup"><span data-stu-id="94309-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="94309-117">**.NET framework sürümleri**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94309-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94309-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94309-118">See Also</span></span>  
 [<span data-ttu-id="94309-119">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94309-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="94309-120">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94309-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
