---
title: IAssemblyName::GetName Yöntemi
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
ms.openlocfilehash: fe0b465d0e15fadde48c2278aa367632bda3f9ef
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473843"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="ea660-102">IAssemblyName::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea660-102">IAssemblyName::GetName Method</span></span>
<span data-ttu-id="ea660-103">Basit, şifrelenmemiş bu başvurduğu derlemenin adını alır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="ea660-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea660-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea660-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea660-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea660-105">Parameters</span></span>  
 `lpcwBuffer`  
 <span data-ttu-id="ea660-106">[out içinde] Boyutu `pwzName` null Sonlandırıcı karakter geniş karakterler dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="ea660-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="ea660-107">[out] Başvurulan derlemenin adını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="ea660-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea660-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea660-108">Requirements</span></span>  
 <span data-ttu-id="ea660-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea660-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea660-110">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ea660-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ea660-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea660-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea660-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea660-112">See also</span></span>
- [<span data-ttu-id="ea660-113">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea660-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
