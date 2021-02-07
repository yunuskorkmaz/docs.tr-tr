---
description: 'Hakkında daha fazla bilgi edinin: ASM_CMP_FLAGS numaralandırması'
title: ASM_CMP_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- ASM_CMP_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CMP_FLAGS
helpviewer_keywords:
- ASM_CMP_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 4d1e6700-d4be-4fbd-8796-bfb4c07abbc8
topic_type:
- apiref
ms.openlocfilehash: 6d35691e853d76dc0e363651b23a6e5ff94244a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761427"
---
# <a name="asm_cmp_flags-enumeration"></a><span data-ttu-id="f8735-103">ASM_CMP_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f8735-103">ASM_CMP_FLAGS Enumeration</span></span>

<span data-ttu-id="f8735-104">[IAssemblyName:: IsEqual](iassemblyname-isequal-method.md) yöntemiyle Karşılaştırılacak iki derlemenin sürümünü, derlemeyi, kültürünü, imzasını, vb. gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8735-104">Indicates the version, build, culture, signature, and so on, of two assemblies to be compared by the [IAssemblyName::IsEqual](iassemblyname-isequal-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8735-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f8735-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    ASM_CMPF_NAME                   = 0x1,  
    ASM_CMPF_MAJOR_VERSION          = 0x2,  
    ASM_CMPF_MINOR_VERSION          = 0x4,  
    ASM_CMPF_BUILD_NUMBER           = 0x8,  
    ASM_CMPF_REVISION_NUMBER        = 0x10,  
  
    ASM_CMPF_VERSION                =
                 ASM_CMPF_MAJOR_VERSION |
                 ASM_CMPF_MINOR_VERSION |
                 ASM_CMPF_BUILD_NUMBER  |
                 ASM_CMPF_REVISION_NUMBER,  
  
    ASM_CMPF_PUBLIC_KEY_TOKEN       = 0x20,  
    ASM_CMPF_CULTURE                = 0x40,  
    ASM_CMPF_CUSTOM                 = 0x80,  
    ASM_CMPF_DEFAULT                = 0x100,  
    ASM_CMPF_RETARGET               = 0x200,  
    ASM_CMPF_ARCHITECTURE           = 0x400,  
    ASM_CMPF_CONFIG_MASK            = 0x800,  
    ASM_CMPF_MVID                   = 0x1000,  
    ASM_CMPF_SIGNATURE              = 0x2000,  
  
    ASM_CMPF_IL_ALL                 =
                 ASM_CMPF_NAME             |
                 ASM_CMPF_VERSION          |
                 ASM_CMPF_PUBLIC_KEY_TOKEN |
                 ASM_CMPF_CULTURE,  
  
    ASM_CMPF_IL_NO_VERSION          =
                 ASM_CMPF_NAME             |
                 ASM_CMPF_PUBLIC_KEY_TOKEN |
                 ASM_CMPF_CULTURE  
  
} ASM_CMP_FLAGS;  
```  
  
## <a name="requirements"></a><span data-ttu-id="f8735-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f8735-106">Requirements</span></span>  

 <span data-ttu-id="f8735-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8735-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8735-108">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f8735-108">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f8735-109">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f8735-109">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8735-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8735-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8735-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8735-111">See also</span></span>

- [<span data-ttu-id="f8735-112">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f8735-112">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="f8735-113">Fusion Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="f8735-113">Fusion Enumerations</span></span>](fusion-enumerations.md)
