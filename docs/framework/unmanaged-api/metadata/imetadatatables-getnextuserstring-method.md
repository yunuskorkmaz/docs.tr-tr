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
ms.openlocfilehash: bb53d980a7b2121854748d5117bc539fed125163
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680371"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="0deef-102">IMetaDataTables::GetNextUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="0deef-102">IMetaDataTables::GetNextUserString Method</span></span>

<span data-ttu-id="0deef-103">Geçerli tablo sütunundaki bir sonraki sabit kodlanmış dizeyi içeren satırın dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="0deef-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0deef-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0deef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0deef-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0deef-105">Parameters</span></span>  

 `ixUserString`  
 <span data-ttu-id="0deef-106">'ndaki Geçerli dize sütunundan bir dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="0deef-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="0deef-107">dışı Sütundaki sonraki dizenin satır dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0deef-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0deef-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0deef-108">Remarks</span></span>  

 <span data-ttu-id="0deef-109">Tutarlı sonuçlar döndürmediğinden bu yöntemin kullanımını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="0deef-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="0deef-110">GUID tablosu hakkında daha fazla bilgi için, bkz. ortak dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği".</span><span class="sxs-lookup"><span data-stu-id="0deef-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="0deef-111">Belgeler çevrimiçi olarak kullanılabilir; bkz. [ecma C# ve ortak dil altyapısı standartları](../../../standard/components.md#applicable-standards) ve [standart ECMA-335-ortak DIL altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="0deef-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0deef-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0deef-112">Requirements</span></span>  

 <span data-ttu-id="0deef-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0deef-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0deef-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0deef-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0deef-115">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0deef-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0deef-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0deef-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0deef-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0deef-117">See also</span></span>

- [<span data-ttu-id="0deef-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0deef-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="0deef-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0deef-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
