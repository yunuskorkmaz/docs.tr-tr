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
ms.openlocfilehash: 2d8cbc540377c8f2a26b8fafef35c19e94a59c51
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536015"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="a8be5-102">IAssemblyName::GetDisplayName Metodu</span><span class="sxs-lookup"><span data-stu-id="a8be5-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="a8be5-103">Okunabilir bu başvurduğu derlemenin adını alır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="a8be5-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8be5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8be5-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8be5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a8be5-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="a8be5-106">[out] Başvurulan derlemenin adını içeren dize arabelleği.</span><span class="sxs-lookup"><span data-stu-id="a8be5-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="a8be5-107">[out içinde] Boyutu `szDisplayName` geniş karakter, bir sonlandırıcı null karakter de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="a8be5-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="a8be5-108">[in] Bitsel bir birleşimi [asm_dısplay_flags](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) özelliklerini etkileyen değerleri `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="a8be5-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8be5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8be5-109">Requirements</span></span>  
 <span data-ttu-id="a8be5-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8be5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8be5-111">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="a8be5-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a8be5-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8be5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8be5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8be5-113">See also</span></span>
- [<span data-ttu-id="a8be5-114">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8be5-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="a8be5-115">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="a8be5-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
