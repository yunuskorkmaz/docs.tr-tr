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
ms.openlocfilehash: 44ae2d16563220f8f5b81b6f609dee7df715fd0e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447399"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="cb53b-102">IMetaDataTables::GetNextUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="cb53b-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="cb53b-103">Geçerli tablo sütunundaki bir sonraki sabit kodlanmış dizeyi içeren satırın dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="cb53b-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb53b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb53b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb53b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb53b-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="cb53b-106">'ndaki Geçerli dize sütunundan bir dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="cb53b-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="cb53b-107">dışı Sütundaki sonraki dizenin satır dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cb53b-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb53b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb53b-108">Remarks</span></span>  
 <span data-ttu-id="cb53b-109">Tutarlı sonuçlar döndürmediğinden bu yöntemin kullanımını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="cb53b-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="cb53b-110">GUID tablosu hakkında daha fazla bilgi için, bkz. ortak dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği".</span><span class="sxs-lookup"><span data-stu-id="cb53b-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="cb53b-111">Belgeler çevrimiçi olarak kullanılabilir; Ecma International web sitesinde, MSDN ve [standart ECMA-335-ortak dil altyapısı (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) üzerinde bulunan [ECMA C# ve ortak dil altyapısı standartlarına](https://go.microsoft.com/fwlink/?LinkID=99212) bakın.</span><span class="sxs-lookup"><span data-stu-id="cb53b-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb53b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb53b-112">Requirements</span></span>  
 <span data-ttu-id="cb53b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb53b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb53b-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cb53b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb53b-115">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="cb53b-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb53b-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb53b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb53b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb53b-117">See also</span></span>

- [<span data-ttu-id="cb53b-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb53b-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="cb53b-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb53b-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
