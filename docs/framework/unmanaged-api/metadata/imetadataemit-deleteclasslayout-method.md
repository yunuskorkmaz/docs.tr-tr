---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D eleteClassLayout yöntemi'
title: IMetaDataEmit::DeleteClassLayout Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteClassLayout
helpviewer_keywords:
- DeleteClassLayout method [.NET Framework metadata]
- IMetaDataEmit::DeleteClassLayout method [.NET Framework metadata]
ms.assetid: 65a4ad49-fa49-4b36-8ed1-76dd6a185ab4
topic_type:
- apiref
ms.openlocfilehash: 44be89f415087a1457a83bb1167e1017d26ed5ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783995"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="b7452-103">IMetaDataEmit::DeleteClassLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7452-103">IMetaDataEmit::DeleteClassLayout Method</span></span>

<span data-ttu-id="b7452-104">Belirtilen belirteçle temsil edilen tür için sınıf düzeni meta veri imzasını yok eder.</span><span class="sxs-lookup"><span data-stu-id="b7452-104">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7452-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7452-105">Syntax</span></span>  
  
```cpp  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7452-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7452-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="b7452-107">'ndaki `mdTypeDef` Sınıf düzeninin silineceği türü temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="b7452-107">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7452-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7452-108">Requirements</span></span>  

 <span data-ttu-id="b7452-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7452-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7452-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b7452-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7452-111">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b7452-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7452-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7452-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7452-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7452-113">See also</span></span>

- [<span data-ttu-id="b7452-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7452-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b7452-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7452-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
