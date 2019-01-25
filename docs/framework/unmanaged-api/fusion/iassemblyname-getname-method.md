---
title: IAssemblyName::GetName Metodu
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7859beae572f05863fb24f0257aae8b0ec16bbcf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640881"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="d10e3-102">IAssemblyName::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="d10e3-102">IAssemblyName::GetName Method</span></span>
<span data-ttu-id="d10e3-103">Basit, şifrelenmemiş bu başvurduğu derlemenin adını alır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="d10e3-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d10e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d10e3-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d10e3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d10e3-105">Parameters</span></span>  
 `lpcwBuffer`  
 <span data-ttu-id="d10e3-106">[out içinde] Boyutu `pwzName` null Sonlandırıcı karakter geniş karakterler dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="d10e3-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="d10e3-107">[out] Başvurulan derlemenin adını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="d10e3-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d10e3-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d10e3-108">Requirements</span></span>  
 <span data-ttu-id="d10e3-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d10e3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d10e3-110">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d10e3-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d10e3-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d10e3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d10e3-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d10e3-112">See also</span></span>
- [<span data-ttu-id="d10e3-113">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d10e3-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
