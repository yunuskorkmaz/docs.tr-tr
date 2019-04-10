---
title: IAssemblyName::GetDisplayName Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 323c883b4010f3ddd4c575e5d5fc40a3419e57c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214370"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="2d4d6-102">IAssemblyName::GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d4d6-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="2d4d6-103">Okunabilir bu başvurduğu derlemenin adını alır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="2d4d6-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d4d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d4d6-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d4d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d4d6-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="2d4d6-106">[out] Başvurulan derlemenin adını içeren dize arabelleği.</span><span class="sxs-lookup"><span data-stu-id="2d4d6-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="2d4d6-107">[out içinde] Boyutu `szDisplayName` geniş karakter, bir sonlandırıcı null karakter de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="2d4d6-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="2d4d6-108">[in] Bitsel bir birleşimi [asm_dısplay_flags](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) özelliklerini etkileyen değerleri `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="2d4d6-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d4d6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d4d6-109">Requirements</span></span>  
 <span data-ttu-id="2d4d6-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d4d6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d4d6-111">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2d4d6-111">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="2d4d6-112">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="2d4d6-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2d4d6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d4d6-113">See also</span></span>

- [<span data-ttu-id="2d4d6-114">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d4d6-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="2d4d6-115">Fusion Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="2d4d6-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
