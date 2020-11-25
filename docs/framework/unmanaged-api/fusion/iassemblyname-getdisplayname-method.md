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
ms.openlocfilehash: 13d71a9da2539c45076e5eb92e153e37c1df4b47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727919"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="c8aa2-102">IAssemblyName::GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8aa2-102">IAssemblyName::GetDisplayName Method</span></span>

<span data-ttu-id="c8aa2-103">Bu [IAssemblyName](iassemblyname-interface.md) nesnesi tarafından başvurulan derlemenin okunabilir adını alır.</span><span class="sxs-lookup"><span data-stu-id="c8aa2-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8aa2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c8aa2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8aa2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8aa2-105">Parameters</span></span>  

 `szDisplayName`  
 <span data-ttu-id="c8aa2-106">dışı Başvurulan derlemenin adını içeren dize arabelleği.</span><span class="sxs-lookup"><span data-stu-id="c8aa2-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="c8aa2-107">[in, out] `szDisplayName` Bir null Sonlandırıcı karakteri de dahil olmak üzere geniş karakter cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="c8aa2-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="c8aa2-108">'ndaki Özelliklerini etkileyen [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) değerlerinin bit düzeyinde birleşimi `szDisplayName` .</span><span class="sxs-lookup"><span data-stu-id="c8aa2-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8aa2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8aa2-109">Requirements</span></span>  

 <span data-ttu-id="c8aa2-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8aa2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8aa2-111">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c8aa2-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c8aa2-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8aa2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8aa2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8aa2-113">See also</span></span>

- [<span data-ttu-id="c8aa2-114">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8aa2-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="c8aa2-115">Fusion Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="c8aa2-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
