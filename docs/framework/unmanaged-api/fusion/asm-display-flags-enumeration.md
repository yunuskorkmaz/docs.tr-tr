---
title: ASM_DISPLAY_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- ASM_DISPLAY_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_DISPLAY_FLAGS
helpviewer_keywords:
- ASM_DISPLAY_FLAGS enumeration [.NET Framework fusion]
ms.assetid: dbade6c9-9d26-4a79-9fd2-46108edd12d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8befdb454a564ec834532653dd44cf230fa43d79
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795209"
---
# <a name="asm_display_flags-enumeration"></a><span data-ttu-id="eb11b-102">ASM_DISPLAY_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="eb11b-102">ASM_DISPLAY_FLAGS Enumeration</span></span>
<span data-ttu-id="eb11b-103">Görünen adı [IAssemblyName:: GetDisplayName](iassemblyname-getdisplayname-method.md) yöntemi tarafından alınacak derlemenin sürümünü, derlemesini, kültürünü, imzasını ve benzerlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb11b-103">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](iassemblyname-getdisplayname-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb11b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb11b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    ASM_DISPLAYF_VERSION                 = 0x01,  
    ASM_DISPLAYF_CULTURE                 = 0x02,  
    ASM_DISPLAYF_PUBLIC_KEY_TOKEN        = 0x04,  
    ASM_DISPLAYF_PUBLIC_KEY              = 0x08,  
    ASM_DISPLAYF_CUSTOM                  = 0x10,  
    ASM_DISPLAYF_PROCESSORARCHITECTURE   = 0x20,  
    ASM_DISPLAYF_LANGUAGEID              = 0x40,  
    ASM_DISPLAYF_RETARGET                = 0x80,  
    ASM_DISPLAYF_CONFIG_MASK             = 0x100,  
    ASM_DISPLAYF_MVID                    = 0x200,  
    ASM_DISPLAYF_FULL                    =   
                      ASM_DISPLAYF_VERSION           |   
                      ASM_DISPLAYF_CULTURE           |   
                      ASM_DISPLAYF_PUBLIC_KEY_TOKEN  |   
                      ASM_DISPLAYF_RETARGET          |   
                      ASM_DISPLAYF_PROCESSORARCHITECTURE  
  
} ASM_DISPLAY_FLAGS;  
```  
  
## <a name="remarks"></a><span data-ttu-id="eb11b-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb11b-105">Remarks</span></span>  
 <span data-ttu-id="eb11b-106">`ASM_DISPLAYF_FULL`[IAssemblyName](iassemblyname-interface.md) nesnesinin sürümünde yapılan tüm değişiklikleri yansıtır.</span><span class="sxs-lookup"><span data-stu-id="eb11b-106">`ASM_DISPLAYF_FULL` reflects any changes made to the version of the [IAssemblyName](iassemblyname-interface.md) object.</span></span> <span data-ttu-id="eb11b-107">Döndürülen değerin sabit olduğunu varsaymayın.</span><span class="sxs-lookup"><span data-stu-id="eb11b-107">Do not assume that the returned value is immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb11b-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb11b-108">Requirements</span></span>  
 <span data-ttu-id="eb11b-109">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb11b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb11b-110">**Üst bilgi** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="eb11b-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="eb11b-111">**Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="eb11b-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eb11b-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb11b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb11b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb11b-113">See also</span></span>

- [<span data-ttu-id="eb11b-114">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb11b-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="eb11b-115">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="eb11b-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
