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
ms.openlocfilehash: 3490eec7c3b59ab8f4158498e2731773b6491b42
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490191"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="79065-102">IMetaDataTables::GetNextUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="79065-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="79065-103">Geçerli tablo sütunundaki bir sonraki sabit kodlanmış dizeyi içeren satırın dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="79065-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79065-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="79065-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79065-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79065-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="79065-106">'ndaki Geçerli dize sütunundan bir dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="79065-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="79065-107">dışı Sütundaki sonraki dizenin satır dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="79065-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79065-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79065-108">Remarks</span></span>  
 <span data-ttu-id="79065-109">Tutarlı sonuçlar döndürmediğinden bu yöntemin kullanımını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="79065-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="79065-110">GUID tablosu hakkında daha fazla bilgi için, bkz. ortak dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği".</span><span class="sxs-lookup"><span data-stu-id="79065-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="79065-111">Belgeler çevrimiçi olarak kullanılabilir; bkz. [ecma C# ve ortak dil altyapısı standartları](../../../standard/components.md#applicable-standards) ve [standart ECMA-335-ortak DIL altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="79065-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79065-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79065-112">Requirements</span></span>  
 <span data-ttu-id="79065-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79065-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79065-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="79065-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="79065-115">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="79065-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="79065-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79065-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79065-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79065-117">See also</span></span>

- [<span data-ttu-id="79065-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79065-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="79065-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79065-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
