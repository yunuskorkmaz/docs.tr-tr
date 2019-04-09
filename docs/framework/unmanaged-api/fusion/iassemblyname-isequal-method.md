---
title: IAssemblyName::IsEqual Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80402234d9374fa4f16e1f8bb315536a9bdfb2c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081521"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="be9ce-102">IAssemblyName::IsEqual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be9ce-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="be9ce-103">Belirtilen bir olup olmadığını belirler [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesnedir şuna eşit `IAssemblyName`bağlı olarak belirtilen karşılaştırma bayrakları.</span><span class="sxs-lookup"><span data-stu-id="be9ce-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be9ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be9ce-104">Syntax</span></span>  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be9ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be9ce-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="be9ce-106">[in] `IAssemblyName` Bu Karşılaştırılacak nesne `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="be9ce-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="be9ce-107">[in] Bitsel bir birleşimi [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) karşılaştırma etkileyen değerleri.</span><span class="sxs-lookup"><span data-stu-id="be9ce-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be9ce-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be9ce-108">Requirements</span></span>  
 <span data-ttu-id="be9ce-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be9ce-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be9ce-110">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="be9ce-110">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="be9ce-111">.NET Framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="be9ce-111">NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="be9ce-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be9ce-112">See also</span></span>

- [<span data-ttu-id="be9ce-113">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be9ce-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="be9ce-114">Fusion Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="be9ce-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
