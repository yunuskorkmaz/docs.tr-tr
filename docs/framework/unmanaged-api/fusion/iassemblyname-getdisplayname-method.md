---
description: ': IAssemblyName:: GetDisplayName metodu hakkında daha fazla bilgi'
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
ms.openlocfilehash: 9b52a901385fa9b3ba7cb6bcd1678d0718f8f695
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760764"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="f12e7-103">IAssemblyName::GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f12e7-103">IAssemblyName::GetDisplayName Method</span></span>

<span data-ttu-id="f12e7-104">Bu [IAssemblyName](iassemblyname-interface.md) nesnesi tarafından başvurulan derlemenin okunabilir adını alır.</span><span class="sxs-lookup"><span data-stu-id="f12e7-104">Gets the human-readable name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f12e7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f12e7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f12e7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f12e7-106">Parameters</span></span>  

 `szDisplayName`  
 <span data-ttu-id="f12e7-107">dışı Başvurulan derlemenin adını içeren dize arabelleği.</span><span class="sxs-lookup"><span data-stu-id="f12e7-107">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="f12e7-108">[in, out] `szDisplayName` Bir null Sonlandırıcı karakteri de dahil olmak üzere geniş karakter cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="f12e7-108">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="f12e7-109">'ndaki Özelliklerini etkileyen [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) değerlerinin bit düzeyinde birleşimi `szDisplayName` .</span><span class="sxs-lookup"><span data-stu-id="f12e7-109">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f12e7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f12e7-110">Requirements</span></span>  

 <span data-ttu-id="f12e7-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f12e7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f12e7-112">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f12e7-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f12e7-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f12e7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12e7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f12e7-114">See also</span></span>

- [<span data-ttu-id="f12e7-115">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f12e7-115">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="f12e7-116">Fusion Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="f12e7-116">Fusion Enumerations</span></span>](fusion-enumerations.md)
