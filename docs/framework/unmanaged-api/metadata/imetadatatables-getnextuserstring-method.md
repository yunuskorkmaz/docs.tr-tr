---
title: IMetaDataTables::GetNextUserString Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetNextUserString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 318bd7d05a7da5ce728ca80fe9bacfd84f501884
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="6df76-102">IMetaDataTables::GetNextUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="6df76-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="6df76-103">Sonraki sabit kodlanmış dize geçerli tablo sütununda içeren satırın dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="6df76-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6df76-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6df76-104">Syntax</span></span>  
  
```  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6df76-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6df76-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="6df76-106">[in] Geçerli dize sütunu bir dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="6df76-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="6df76-107">[out] Satır dizini sütun sonraki dizesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6df76-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6df76-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6df76-108">Remarks</span></span>  
 <span data-ttu-id="6df76-109">Tutarlı sonuçlar döndürmüyor olduğundan, bu yöntemin kullanılması önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="6df76-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="6df76-110">GUID tablosu hakkında daha fazla bilgi için özellikle "Bölüm II: meta veri tanım ve semantiği" ortak dil altyapısı (CLI) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="6df76-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="6df76-111">Belge çevrimiçi kullanılabilir; bkz: [ECMA C# ve ortak dil altyapısı standartları](http://go.microsoft.com/fwlink/?LinkID=99212) MSDN'de ve [standart ECMA-335 - ortak dil altyapısı (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) Ecma uluslararası Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="6df76-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6df76-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6df76-112">Requirements</span></span>  
 <span data-ttu-id="6df76-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6df76-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6df76-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6df76-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6df76-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6df76-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6df76-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6df76-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df76-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6df76-117">See Also</span></span>  
 [<span data-ttu-id="6df76-118">Imetadatatables arabirimi</span><span class="sxs-lookup"><span data-stu-id="6df76-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="6df76-119">Imetadatatables2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="6df76-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
