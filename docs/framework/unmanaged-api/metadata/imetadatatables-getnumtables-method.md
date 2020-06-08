---
title: IMetaDataTables::GetNumTables Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNumTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNumTables
helpviewer_keywords:
- GetNumTables method [.NET Framework metadata]
- IMetaDataTables::GetNumTables method [.NET Framework metadata]
ms.assetid: 8196f2a3-bbf2-45d3-a6cd-74502c356644
topic_type:
- apiref
ms.openlocfilehash: df02def0c14beb4e9ffd1b9260002767586a59b5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490204"
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="72010-102">IMetaDataTables::GetNumTables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72010-102">IMetaDataTables::GetNumTables Method</span></span>
<span data-ttu-id="72010-103">Geçerli örnek kapsamındaki tablo sayısını alır `IMetaDataTables` .</span><span class="sxs-lookup"><span data-stu-id="72010-103">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72010-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="72010-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72010-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72010-105">Parameters</span></span>  
 `pcTables`  
 <span data-ttu-id="72010-106">dışı Geçerli örnek kapsamındaki tablo sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="72010-106">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72010-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72010-107">Requirements</span></span>  
 <span data-ttu-id="72010-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72010-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72010-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="72010-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72010-110">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="72010-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72010-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72010-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72010-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72010-112">See also</span></span>

- [<span data-ttu-id="72010-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72010-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="72010-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72010-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
