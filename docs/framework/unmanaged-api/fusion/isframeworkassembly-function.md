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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e231c4fa51e6e66cba6227233cf73dd1cd4ebbe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733928"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="06c55-102">IsFrameworkAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="06c55-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="06c55-103">Belirtilen derleme yönetilip yönetilmediğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="06c55-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06c55-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06c55-104">Syntax</span></span>  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06c55-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06c55-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="06c55-106">[in] Denetlenecek derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="06c55-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="06c55-107">[out] Derleme yönetilip yönetilmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="06c55-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="06c55-108">[in] Derlemenin benzersiz kimliği içeren uncanonicalized bir dize.</span><span class="sxs-lookup"><span data-stu-id="06c55-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="06c55-109">[in] Boyutu `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="06c55-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06c55-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06c55-110">Remarks</span></span>  
 <span data-ttu-id="06c55-111">`pwzAssemblyReference` Parametresi, bir derlemenin adını içeren bir karakter dizesine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="06c55-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="06c55-112">Bu derleme parçasıysa .NET Framework'ün `pbIsFrameworkAssembly` parametresi bir Boolean değerini içerecek `true`.</span><span class="sxs-lookup"><span data-stu-id="06c55-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="06c55-113">Adlandırılmış derlemeyi .NET Framework'ün bir parçası değilse veya `pwzAssemblyReference` parametre, bir derleme adı değil `pbIsFrameworkAssembly` Boolean değerini içerecek `false`.</span><span class="sxs-lookup"><span data-stu-id="06c55-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06c55-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06c55-114">Requirements</span></span>  
 <span data-ttu-id="06c55-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06c55-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06c55-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06c55-116">See also</span></span>
- [<span data-ttu-id="06c55-117">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="06c55-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
