---
title: IMetaDataTables::GetNextGuid Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
ms.openlocfilehash: d4055975287267d08d2c2224ff6ddaa39fca548d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937794"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="381b7-102">IMetaDataTables::GetNextGuid Metodu</span><span class="sxs-lookup"><span data-stu-id="381b7-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="381b7-103">Geçerli tablo sütunundaki sonraki GUID değerinin dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="381b7-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="381b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="381b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="381b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="381b7-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="381b7-106">'ndaki Bir GUID tablo sütunundaki dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="381b7-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="381b7-107">dışı Sonraki GUID değerinin dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="381b7-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="381b7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="381b7-108">Remarks</span></span>  

  <span data-ttu-id="381b7-109">Tutarlı sonuçlar döndürmediğinden bu yöntemin kullanımını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="381b7-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="381b7-110">GUID tablosu hakkında daha fazla bilgi için, bkz. ortak dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği".</span><span class="sxs-lookup"><span data-stu-id="381b7-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="381b7-111">Belgeler çevrimiçi olarak kullanılabilir; bkz [. C# ECMA ve ortak dil altyapısı STANDARTLARı](../../../standard/components.md#applicable-standards) ve [standart ECMA-335-ortak dil altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="381b7-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="381b7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="381b7-112">Requirements</span></span>  
 <span data-ttu-id="381b7-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="381b7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="381b7-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="381b7-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="381b7-115">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="381b7-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="381b7-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="381b7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="381b7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="381b7-117">See also</span></span>

- [<span data-ttu-id="381b7-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="381b7-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="381b7-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="381b7-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
