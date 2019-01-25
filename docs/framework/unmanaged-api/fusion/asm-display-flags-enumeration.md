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
ms.openlocfilehash: 0871a06c6e27089d9e8fea6726d1d7b37fb75120
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561757"
---
# <a name="asmdisplayflags-enumeration"></a><span data-ttu-id="9a575-102">ASM_DISPLAY_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9a575-102">ASM_DISPLAY_FLAGS Enumeration</span></span>
<span data-ttu-id="9a575-103">Sürüm, derleme, kültür, imza ve benzeri, derlemenin görünen adı tarafından alınabilir gösterir [Iassemblyname::getdisplayname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9a575-103">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a575-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a575-104">Syntax</span></span>  
  
```  
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
  
## <a name="remarks"></a><span data-ttu-id="9a575-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a575-105">Remarks</span></span>  
 <span data-ttu-id="9a575-106">`ASM_DISPLAYF_FULL` sürümünde yapılan tüm değişiklikleri yansıtır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="9a575-106">`ASM_DISPLAYF_FULL` reflects any changes made to the version of the [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span> <span data-ttu-id="9a575-107">Döndürülen değer sabittir varsaymayın.</span><span class="sxs-lookup"><span data-stu-id="9a575-107">Do not assume that the returned value is immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a575-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a575-108">Requirements</span></span>  
 <span data-ttu-id="9a575-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a575-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a575-110">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="9a575-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9a575-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9a575-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a575-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a575-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a575-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a575-113">See also</span></span>
- [<span data-ttu-id="9a575-114">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a575-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="9a575-115">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="9a575-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
