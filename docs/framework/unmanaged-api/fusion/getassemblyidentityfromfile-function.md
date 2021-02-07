---
description: ': GetAssemblyIdentityFromFile Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 8832e03182a5652c938404c99115fa8059439d1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761046"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="3fcf4-103">GetAssemblyIdentityFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="3fcf4-103">GetAssemblyIdentityFromFile Function</span></span>

<span data-ttu-id="3fcf4-104">`IUnknown`Belirtilen dosya yolundaki derlemede belirtilen bir nesneye yönelik bir işaretçi alır `IID` .</span><span class="sxs-lookup"><span data-stu-id="3fcf4-104">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fcf4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fcf4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fcf4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3fcf4-106">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="3fcf4-107">'ndaki İstenen derleme için geçerli bir yol.</span><span class="sxs-lookup"><span data-stu-id="3fcf4-107">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="3fcf4-108">'ndaki `IID` Döndürülecek arabirim.</span><span class="sxs-lookup"><span data-stu-id="3fcf4-108">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="3fcf4-109">dışı Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3fcf4-109">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fcf4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3fcf4-110">Requirements</span></span>  

 <span data-ttu-id="3fcf4-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fcf4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fcf4-112">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="3fcf4-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="3fcf4-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fcf4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fcf4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fcf4-114">See also</span></span>

- [<span data-ttu-id="3fcf4-115">IUnknown</span><span class="sxs-lookup"><span data-stu-id="3fcf4-115">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="3fcf4-116">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3fcf4-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
