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
ms.openlocfilehash: 6522dbc8e49d612fc4c0d9597a9b5f12edb2cfe1
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937782"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="98c2a-102">IMetaDataTables::GetNextUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="98c2a-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="98c2a-103">Geçerli tablo sütunundaki bir sonraki sabit kodlanmış dizeyi içeren satırın dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="98c2a-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98c2a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98c2a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98c2a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98c2a-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="98c2a-106">'ndaki Geçerli dize sütunundan bir dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="98c2a-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="98c2a-107">dışı Sütundaki sonraki dizenin satır dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="98c2a-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98c2a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98c2a-108">Remarks</span></span>  
 <span data-ttu-id="98c2a-109">Tutarlı sonuçlar döndürmediğinden bu yöntemin kullanımını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="98c2a-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="98c2a-110">GUID tablosu hakkında daha fazla bilgi için, bkz. ortak dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği".</span><span class="sxs-lookup"><span data-stu-id="98c2a-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="98c2a-111">Belgeler çevrimiçi olarak kullanılabilir; bkz [. C# ECMA ve ortak dil altyapısı STANDARTLARı](../../../standard/components.md#applicable-standards) ve [standart ECMA-335-ortak dil altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="98c2a-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98c2a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98c2a-112">Requirements</span></span>  
 <span data-ttu-id="98c2a-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98c2a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98c2a-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="98c2a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98c2a-115">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="98c2a-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="98c2a-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98c2a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98c2a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98c2a-117">See also</span></span>

- [<span data-ttu-id="98c2a-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98c2a-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="98c2a-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98c2a-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
