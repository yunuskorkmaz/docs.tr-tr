---
title: IMetaDataTables::GetGuid Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 2ac29de437e746f1524fc1427c47eb8f5c761be7
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937804"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="ec703-102">IMetaDataTables::GetGuid Metodu</span><span class="sxs-lookup"><span data-stu-id="ec703-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="ec703-103">Belirtilen dizindeki satırdan bir GUID alır.</span><span class="sxs-lookup"><span data-stu-id="ec703-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec703-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec703-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec703-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec703-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="ec703-106">'ndaki GUID 'nin alınacağı satırın dizini.</span><span class="sxs-lookup"><span data-stu-id="ec703-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="ec703-107">dışı GUID işaretçisinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ec703-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec703-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec703-108">Remarks</span></span>  

  <span data-ttu-id="ec703-109">Tutarlı sonuçlar döndürmediğinden bu yöntemin kullanımını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="ec703-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="ec703-110">GUID tablosu hakkında daha fazla bilgi için, bkz. ortak dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği".</span><span class="sxs-lookup"><span data-stu-id="ec703-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="ec703-111">Belgeler çevrimiçi olarak kullanılabilir; bkz [. C# ECMA ve ortak dil altyapısı STANDARTLARı](../../../standard/components.md#applicable-standards) ve [standart ECMA-335-ortak dil altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="ec703-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec703-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec703-112">Requirements</span></span>  
 <span data-ttu-id="ec703-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec703-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec703-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ec703-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec703-115">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ec703-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec703-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec703-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec703-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec703-117">See also</span></span>

- [<span data-ttu-id="ec703-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec703-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="ec703-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec703-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
