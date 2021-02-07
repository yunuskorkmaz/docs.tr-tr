---
description: ': IMetaDataTables:: GetNextUserString metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: cba1fad18b4f697a5e48ad3b0676bf93f9c66e4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687967"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="e9627-103">IMetaDataTables::GetNextUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="e9627-103">IMetaDataTables::GetNextUserString Method</span></span>

<span data-ttu-id="e9627-104">Geçerli tablo sütunundaki bir sonraki sabit kodlanmış dizeyi içeren satırın dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="e9627-104">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9627-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9627-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9627-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9627-106">Parameters</span></span>  

 `ixUserString`  
 <span data-ttu-id="e9627-107">'ndaki Geçerli dize sütunundan bir dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="e9627-107">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="e9627-108">dışı Sütundaki sonraki dizenin satır dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e9627-108">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9627-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9627-109">Remarks</span></span>  

 <span data-ttu-id="e9627-110">Tutarlı sonuçlar döndürmediğinden bu yöntemin kullanımını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="e9627-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="e9627-111">GUID tablosu hakkında daha fazla bilgi için, bkz. ortak dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği".</span><span class="sxs-lookup"><span data-stu-id="e9627-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="e9627-112">Belgeler çevrimiçi olarak kullanılabilir; bkz. [ecma C# ve ortak dil altyapısı standartları](../../../standard/components.md#applicable-standards) ve [standart ECMA-335-ortak DIL altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="e9627-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9627-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9627-113">Requirements</span></span>  

 <span data-ttu-id="e9627-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9627-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9627-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e9627-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e9627-116">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e9627-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e9627-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9627-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9627-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9627-118">See also</span></span>

- [<span data-ttu-id="e9627-119">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9627-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="e9627-120">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9627-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
