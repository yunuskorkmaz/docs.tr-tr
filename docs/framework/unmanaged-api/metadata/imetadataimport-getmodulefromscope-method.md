---
description: ': IMetaDataImport:: GetModuleFromScope yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::GetModuleFromScope Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
ms.openlocfilehash: 8c1e952a45b3827717102428fbd18ceac3951baf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753373"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="e52b4-103">IMetaDataImport::GetModuleFromScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e52b4-103">IMetaDataImport::GetModuleFromScope Method</span></span>

<span data-ttu-id="e52b4-104">Geçerli meta veri kapsamında başvurulan modül için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="e52b4-104">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e52b4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e52b4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e52b4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e52b4-106">Parameters</span></span>  

 `pmd`  
 <span data-ttu-id="e52b4-107">dışı Geçerli meta veri kapsamında başvurulan modülü temsil eden belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e52b4-107">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e52b4-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e52b4-108">Requirements</span></span>  

 <span data-ttu-id="e52b4-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e52b4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e52b4-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e52b4-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e52b4-111">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e52b4-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e52b4-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e52b4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e52b4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e52b4-113">See also</span></span>

- [<span data-ttu-id="e52b4-114">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e52b4-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e52b4-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e52b4-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
