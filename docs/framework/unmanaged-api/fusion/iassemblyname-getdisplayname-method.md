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
ms.openlocfilehash: 5dbb5dc483bc5a08c59606654d55b5a62266e509
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134377"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="f5707-102">IAssemblyName::GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5707-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="f5707-103">Bu [IAssemblyName](iassemblyname-interface.md) nesnesi tarafından başvurulan derlemenin okunabilir adını alır.</span><span class="sxs-lookup"><span data-stu-id="f5707-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5707-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5707-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5707-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5707-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="f5707-106">dışı Başvurulan derlemenin adını içeren dize arabelleği.</span><span class="sxs-lookup"><span data-stu-id="f5707-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="f5707-107">[in, out] `szDisplayName`, null Sonlandırıcı karakteri de dahil olmak üzere geniş karakter cinsinden boyutudur.</span><span class="sxs-lookup"><span data-stu-id="f5707-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="f5707-108">'ndaki `szDisplayName`özelliklerini etkileyen [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="f5707-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5707-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5707-109">Requirements</span></span>  
 <span data-ttu-id="f5707-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5707-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5707-111">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f5707-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f5707-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5707-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5707-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5707-113">See also</span></span>

- [<span data-ttu-id="f5707-114">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5707-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="f5707-115">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f5707-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
