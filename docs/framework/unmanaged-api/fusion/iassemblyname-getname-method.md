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
ms.openlocfilehash: a2c5c3bbbcf3cf4b87a5f68006c1625666d13926
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753892"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="ab889-102">IAssemblyName::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab889-102">IAssemblyName::GetName Method</span></span>
<span data-ttu-id="ab889-103">Basit, şifrelenmemiş bu başvurduğu derlemenin adını alır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="ab889-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab889-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab889-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab889-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab889-105">Parameters</span></span>  
 `lpcwBuffer`  
 <span data-ttu-id="ab889-106">[out içinde] Boyutu `pwzName` null Sonlandırıcı karakter geniş karakterler dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="ab889-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="ab889-107">[out] Başvurulan derlemenin adını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="ab889-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab889-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab889-108">Requirements</span></span>  
 <span data-ttu-id="ab889-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab889-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab889-110">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ab889-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ab889-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab889-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab889-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab889-112">See also</span></span>

- [<span data-ttu-id="ab889-113">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab889-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
