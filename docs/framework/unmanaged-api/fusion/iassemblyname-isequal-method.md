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
ms.openlocfilehash: 043394541f5ed91b85a57f4cb13c61cca442bfec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431847"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="b5792-102">IAssemblyName::IsEqual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5792-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="b5792-103">Belirtilen bir olup olmadığını belirleyen [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesnesidir için eşit `IAssemblyName`, belirtilen karşılaştırma bayrakları göre.</span><span class="sxs-lookup"><span data-stu-id="b5792-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5792-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5792-104">Syntax</span></span>  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5792-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b5792-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="b5792-106">[in] `IAssemblyName` Bu karşılaştırma yapılacak nesne `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="b5792-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="b5792-107">[in] Bit düzeyinde bileşimini [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) karşılaştırma etkilemek değerleri.</span><span class="sxs-lookup"><span data-stu-id="b5792-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5792-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5792-108">Requirements</span></span>  
 <span data-ttu-id="b5792-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5792-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5792-110">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b5792-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b5792-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5792-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5792-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5792-112">See Also</span></span>  
 [<span data-ttu-id="b5792-113">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5792-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="b5792-114">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b5792-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
