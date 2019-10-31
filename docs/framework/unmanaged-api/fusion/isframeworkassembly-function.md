---
title: IsFrameworkAssembly İşlevi
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
ms.openlocfilehash: e30b6f2d2254d2d107c4c82a2c5664850ce6ec23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123063"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="d84e0-102">IsFrameworkAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="d84e0-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="d84e0-103">Belirtilen derlemenin yönetilip yönetilmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d84e0-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d84e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d84e0-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d84e0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d84e0-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="d84e0-106">'ndaki Denetlenecek derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="d84e0-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="d84e0-107">dışı Derlemenin yönetilip yönetilmediğini gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d84e0-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="d84e0-108">'ndaki Derlemenin benzersiz kimliğini içeren bir Uncanonicalized dizesi.</span><span class="sxs-lookup"><span data-stu-id="d84e0-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="d84e0-109">'ndaki `pwzFrameworkAssemblyIdentity`boyutu.</span><span class="sxs-lookup"><span data-stu-id="d84e0-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d84e0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d84e0-110">Remarks</span></span>  
 <span data-ttu-id="d84e0-111">`pwzAssemblyReference` parametresi, bir derlemenin adını içeren bir karakter dizesinin bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="d84e0-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="d84e0-112">Bu derleme .NET Framework bir parçasıysa, `pbIsFrameworkAssembly` parametresi bir `true`Boolean değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="d84e0-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="d84e0-113">Adlandırılmış derleme .NET Framework bir parçası değilse veya `pwzAssemblyReference` parametresi bir derlemeyi isimlendirilemez `pbIsFrameworkAssembly` Boolean değeri `false`içerecektir.</span><span class="sxs-lookup"><span data-stu-id="d84e0-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d84e0-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d84e0-114">Requirements</span></span>  
 <span data-ttu-id="d84e0-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d84e0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d84e0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d84e0-116">See also</span></span>

- [<span data-ttu-id="d84e0-117">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d84e0-117">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
