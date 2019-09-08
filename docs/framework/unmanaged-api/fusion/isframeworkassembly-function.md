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
ms.openlocfilehash: 269e3702c21532f377735ba6087abb1603dde4f7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796322"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="8f719-102">IsFrameworkAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="8f719-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="8f719-103">Belirtilen derlemenin yönetilip yönetilmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="8f719-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f719-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f719-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f719-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f719-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="8f719-106">'ndaki Denetlenecek derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="8f719-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="8f719-107">dışı Derlemenin yönetilip yönetilmediğini gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="8f719-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="8f719-108">'ndaki Derlemenin benzersiz kimliğini içeren bir Uncanonicalized dizesi.</span><span class="sxs-lookup"><span data-stu-id="8f719-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="8f719-109">'ndaki Boyutu `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="8f719-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f719-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f719-110">Remarks</span></span>  
 <span data-ttu-id="8f719-111">`pwzAssemblyReference` Parametresi, bir derlemenin adını içeren bir karakter dizesinin bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="8f719-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="8f719-112">Bu derleme .NET Framework bir parçasıysa, `pbIsFrameworkAssembly` parametresi bir Boolean `true`değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="8f719-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="8f719-113">Adlandırılmış derleme .NET Framework bir parçası değilse veya `pwzAssemblyReference` parametre bir derlemeyi isimlendirilemez, `pbIsFrameworkAssembly` Boolean değeri `false`içerir.</span><span class="sxs-lookup"><span data-stu-id="8f719-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f719-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f719-114">Requirements</span></span>  
 <span data-ttu-id="8f719-115">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f719-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f719-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f719-116">See also</span></span>

- [<span data-ttu-id="8f719-117">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="8f719-117">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
