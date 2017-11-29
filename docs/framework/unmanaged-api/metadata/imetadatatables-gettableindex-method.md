---
title: IMetaDataTables::GetTableIndex Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetTableIndex
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetTableIndex
helpviewer_keywords:
- GetTableIndex method [.NET Framework metadata]
- IMetaDataTables::GetTableIndex method [.NET Framework metadata]
ms.assetid: c6ec3800-e0d9-4387-afb8-ddc0b818114c
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d49e1258011d68a6278d1c40500386024a2cb0d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="8fb1a-102">IMetaDataTables::GetTableIndex Metodu</span><span class="sxs-lookup"><span data-stu-id="8fb1a-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="8fb1a-103">Belirtilen belirteç tarafından başvurulan tablo için dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="8fb1a-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fb1a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8fb1a-104">Syntax</span></span>  
  
```  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8fb1a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8fb1a-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="8fb1a-106">[in] Bir tabloya başvuruyorsa belirteci.</span><span class="sxs-lookup"><span data-stu-id="8fb1a-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="8fb1a-107">[out] Başvurulan tablo için döndürülen dizin için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8fb1a-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fb1a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fb1a-108">Remarks</span></span>  
 <span data-ttu-id="8fb1a-109">Tutarlı sonuçlar döndürmüyor olduğundan, bu yöntemin kullanılması önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="8fb1a-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="8fb1a-110">GUID tablosu hakkında daha fazla bilgi için özellikle "Bölüm II: meta veri tanım ve semantiği" ortak dil altyapısı (CLI) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="8fb1a-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="8fb1a-111">Belge çevrimiçi kullanılabilir; bkz: [ECMA C# ve ortak dil altyapısı standartları](http://go.microsoft.com/fwlink/?LinkID=99212) MSDN'de ve [standart ECMA-335 - ortak dil altyapısı (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) Ecma uluslararası Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="8fb1a-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fb1a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8fb1a-112">Requirements</span></span>  
 <span data-ttu-id="8fb1a-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fb1a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fb1a-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8fb1a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8fb1a-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8fb1a-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8fb1a-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fb1a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fb1a-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8fb1a-117">See Also</span></span>  
 [<span data-ttu-id="8fb1a-118">Imetadatatables arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fb1a-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="8fb1a-119">Imetadatatables2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fb1a-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
