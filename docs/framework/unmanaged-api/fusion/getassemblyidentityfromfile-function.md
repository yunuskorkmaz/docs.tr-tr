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
ms.openlocfilehash: 50ec5a23db4d2460480bcc3e463ecd88e7470bde
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134529"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="69f02-102">GetAssemblyIdentityFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="69f02-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="69f02-103">Belirtilen dosya yolundaki derlemede belirtilen `IID` sahip bir `IUnknown` nesnesine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="69f02-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f02-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69f02-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="69f02-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69f02-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="69f02-106">'ndaki İstenen derleme için geçerli bir yol.</span><span class="sxs-lookup"><span data-stu-id="69f02-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="69f02-107">'ndaki Döndürülecek arabirimin `IID`.</span><span class="sxs-lookup"><span data-stu-id="69f02-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="69f02-108">dışı Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="69f02-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69f02-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69f02-109">Requirements</span></span>  
 <span data-ttu-id="69f02-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69f02-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69f02-111">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="69f02-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="69f02-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69f02-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69f02-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69f02-113">See also</span></span>

- [<span data-ttu-id="69f02-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="69f02-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="69f02-115">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="69f02-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
