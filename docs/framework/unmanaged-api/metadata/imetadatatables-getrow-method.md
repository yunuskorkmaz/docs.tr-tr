---
title: IMetaDataTables::GetRow Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 760bee2c4a6a6efb16a32579578ab4953492c48e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="2ddef-102">IMetaDataTables::GetRow Metodu</span><span class="sxs-lookup"><span data-stu-id="2ddef-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="2ddef-103">Belirtilen satır dizininde belirtilen tablo dizinindeki tablosundaki satır alır.</span><span class="sxs-lookup"><span data-stu-id="2ddef-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ddef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ddef-104">Syntax</span></span>  
  
```  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ddef-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ddef-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="2ddef-106">[in] Tablonun satır alınır dizini.</span><span class="sxs-lookup"><span data-stu-id="2ddef-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="2ddef-107">[in] Alınacak satır dizini.</span><span class="sxs-lookup"><span data-stu-id="2ddef-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="2ddef-108">[out] Satır için bir işaretçi bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2ddef-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ddef-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ddef-109">Remarks</span></span>  
 <span data-ttu-id="2ddef-110">Tutarlı sonuçlar döndürmüyor olduğundan, bu yöntemin kullanılması önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="2ddef-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="2ddef-111">GUID tablosu hakkında daha fazla bilgi için özellikle "Bölüm II: meta veri tanım ve semantiği" ortak dil altyapısı (CLI) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="2ddef-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="2ddef-112">Belge çevrimiçi kullanılabilir; bkz: [ECMA C# ve ortak dil altyapısı standartları](http://go.microsoft.com/fwlink/?LinkID=99212) MSDN'de ve [standart ECMA-335 - ortak dil altyapısı (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) Ecma uluslararası Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="2ddef-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ddef-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ddef-113">Requirements</span></span>  
 <span data-ttu-id="2ddef-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ddef-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ddef-115">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2ddef-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2ddef-116">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2ddef-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ddef-117">**.NET framework sürümleri**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ddef-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ddef-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ddef-118">See Also</span></span>  
 [<span data-ttu-id="2ddef-119">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ddef-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="2ddef-120">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ddef-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
