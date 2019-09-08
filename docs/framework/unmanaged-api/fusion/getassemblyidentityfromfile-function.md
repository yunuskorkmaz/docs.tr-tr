---
title: GetAssemblyIdentityFromFile İşlevi
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2657ac619bb86bc200de9ce229bf82e4339f78d6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796289"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="0755d-102">GetAssemblyIdentityFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="0755d-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="0755d-103">Belirtilen dosya yolundaki derlemede belirtilen `IUnknown` `IID` bir nesneye yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="0755d-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0755d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0755d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="0755d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0755d-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="0755d-106">'ndaki İstenen derleme için geçerli bir yol.</span><span class="sxs-lookup"><span data-stu-id="0755d-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="0755d-107">'ndaki `IID` Döndürülecek arabirim.</span><span class="sxs-lookup"><span data-stu-id="0755d-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="0755d-108">dışı Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0755d-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0755d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0755d-109">Requirements</span></span>  
 <span data-ttu-id="0755d-110">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0755d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0755d-111">**Üst bilgi** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="0755d-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0755d-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0755d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0755d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0755d-113">See also</span></span>

- [<span data-ttu-id="0755d-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="0755d-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="0755d-115">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0755d-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
