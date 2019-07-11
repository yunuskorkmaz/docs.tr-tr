---
title: ASM_NAME Numaralandırması
ms.date: 03/30/2017
api_name:
- ASM_NAME
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_NAME
helpviewer_keywords:
- ASM_NAME enumeration [.NET Framework fusion]
ms.assetid: c8b65b19-d777-428f-bc0c-0d84c78a37bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06d734bfd79e7752db427821a6ddc663b6e22b7d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778540"
---
# <a name="asmname-enumeration"></a><span data-ttu-id="fe84e-102">ASM_NAME Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fe84e-102">ASM_NAME Enumeration</span></span>
<span data-ttu-id="fe84e-103">Sürüm, yapı, kültür, imza ve özelliklerini alınan veya belirlenen bütünleştirilmiş kodun belirli bir benzeri belirten [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="fe84e-103">Indicates the version, build, culture, signature, and so on, of the assembly whose properties will be retrieved or set by [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe84e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe84e-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    ASM_NAME_PUBLIC_KEY = 0,  
    ASM_NAME_PUBLIC_KEY_TOKEN,  
    ASM_NAME_HASH_VALUE,  
    ASM_NAME_NAME,  
    ASM_NAME_MAJOR_VERSION,  
    ASM_NAME_MINOR_VERSION,  
    ASM_NAME_BUILD_NUMBER,  
    ASM_NAME_REVISION_NUMBER,  
    ASM_NAME_CULTURE,  
    ASM_NAME_PROCESSOR_ID_ARRAY,  
    ASM_NAME_OSINFO_ARRAY,  
    ASM_NAME_HASH_ALGID,  
    ASM_NAME_ALIAS,  
    ASM_NAME_CODEBASE_URL,  
    ASM_NAME_CODEBASE_LASTMOD,  
    ASM_NAME_NULL_PUBLIC_KEY,  
    ASM_NAME_NULL_PUBLIC_KEY_TOKEN,  
    ASM_NAME_CUSTOM,  
    ASM_NAME_NULL_CUSTOM,   
    ASM_NAME_MVID,  
    ASM_NAME_FILE_MAJOR_VERSION,  
    ASM_NAME_FILE_MINOR_VERSION,  
    ASM_NAME_FILE_BUILD_NUMBER,  
    ASM_NAME_FILE_REVISION_NUMBER,  
    ASM_NAME_RETARGET,  
    ASM_NAME_SIGNATURE_BLOB,  
    ASM_NAME_CONFIG_MASK,  
    ASM_NAME_ARCHITECTURE,  
    ASM_NAME_MAX_PARAMS  
  
} ASM_NAME;  
```  
  
## <a name="requirements"></a><span data-ttu-id="fe84e-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe84e-105">Requirements</span></span>  
 <span data-ttu-id="fe84e-106">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe84e-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe84e-107">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="fe84e-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="fe84e-108">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fe84e-108">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fe84e-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe84e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe84e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe84e-110">See also</span></span>

- [<span data-ttu-id="fe84e-111">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe84e-111">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="fe84e-112">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fe84e-112">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
