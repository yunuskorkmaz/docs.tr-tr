---
title: IAssemblyName::GetDisplayName Metodu
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
ms.openlocfilehash: 00a95646323a5ee08d6758b0f6a7c493c661705d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431782"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="6ae9b-102">IAssemblyName::GetDisplayName Metodu</span><span class="sxs-lookup"><span data-stu-id="6ae9b-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="6ae9b-103">Bu tarafından başvurulan derleme okunabilir adını alır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6ae9b-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ae9b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ae9b-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ae9b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ae9b-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="6ae9b-106">[out] Başvurulan derlemeyi adını içeren bir dize arabellek.</span><span class="sxs-lookup"><span data-stu-id="6ae9b-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="6ae9b-107">[içinde out] Boyutunu `szDisplayName` null Sonlandırıcı karakteri geniş karakter dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="6ae9b-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="6ae9b-108">[in] Bit düzeyinde bileşimini [asm_dısplay_flags](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) özelliklerini etkileyen değerleri `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="6ae9b-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ae9b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ae9b-109">Requirements</span></span>  
 <span data-ttu-id="6ae9b-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ae9b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ae9b-111">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6ae9b-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6ae9b-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ae9b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ae9b-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ae9b-113">See Also</span></span>  
 [<span data-ttu-id="6ae9b-114">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ae9b-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="6ae9b-115">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6ae9b-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
