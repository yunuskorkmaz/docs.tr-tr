---
title: IMetaDataTables::GetNextUserString Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b9e729732175b7249e4d3be91996bc5e4050855
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450212"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="e6e66-102">IMetaDataTables::GetNextUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="e6e66-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="e6e66-103">Sonraki sabit kodlanmış dize geçerli tablo sütununda içeren satırın dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="e6e66-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6e66-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6e66-104">Syntax</span></span>  
  
```  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6e66-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6e66-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="e6e66-106">[in] Geçerli dize sütunu bir dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="e6e66-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="e6e66-107">[out] Satır dizini sütun sonraki dizesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e6e66-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6e66-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6e66-108">Remarks</span></span>  
 <span data-ttu-id="e6e66-109">Tutarlı sonuçlar döndürmüyor olduğundan, bu yöntemin kullanılması önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="e6e66-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="e6e66-110">GUID tablosu hakkında daha fazla bilgi için özellikle "Bölüm II: meta veri tanım ve semantiği" ortak dil altyapısı (CLI) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="e6e66-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="e6e66-111">Belge çevrimiçi kullanılabilir; bkz: [ECMA C# ve ortak dil altyapısı standartları](http://go.microsoft.com/fwlink/?LinkID=99212) MSDN'de ve [standart ECMA-335 - ortak dil altyapısı (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) Ecma uluslararası Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="e6e66-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6e66-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6e66-112">Requirements</span></span>  
 <span data-ttu-id="e6e66-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6e66-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6e66-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e6e66-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e6e66-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e6e66-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e6e66-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6e66-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e66-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6e66-117">See Also</span></span>  
 [<span data-ttu-id="e6e66-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6e66-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="e6e66-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6e66-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
