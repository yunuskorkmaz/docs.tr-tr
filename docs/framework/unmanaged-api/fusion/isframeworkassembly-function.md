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
ms.openlocfilehash: 828c7660d6c006e700302d119ce4caf7d76e5d84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728569"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="f5f7c-102">IsFrameworkAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="f5f7c-102">IsFrameworkAssembly Function</span></span>

<span data-ttu-id="f5f7c-103">Belirtilen derlemenin yönetilip yönetilmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f5f7c-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5f7c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f5f7c-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5f7c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5f7c-105">Parameters</span></span>  

 `pwzAssemblyReference`  
 <span data-ttu-id="f5f7c-106">'ndaki Denetlenecek derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="f5f7c-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="f5f7c-107">dışı Derlemenin yönetilip yönetilmediğini gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f5f7c-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="f5f7c-108">'ndaki Derlemenin benzersiz kimliğini içeren bir Uncanonicalized dizesi.</span><span class="sxs-lookup"><span data-stu-id="f5f7c-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="f5f7c-109">'ndaki Boyutu `pwzFrameworkAssemblyIdentity` .</span><span class="sxs-lookup"><span data-stu-id="f5f7c-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5f7c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5f7c-110">Remarks</span></span>  

 <span data-ttu-id="f5f7c-111">Parametresi, bir `pwzAssemblyReference` derlemenin adını içeren bir karakter dizesinin bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="f5f7c-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="f5f7c-112">Bu derleme .NET Framework bir parçasıysa, `pbIsFrameworkAssembly` parametresi bir Boolean değeri içerir `true` .</span><span class="sxs-lookup"><span data-stu-id="f5f7c-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="f5f7c-113">Adlandırılmış derleme .NET Framework bir parçası değilse veya `pwzAssemblyReference` parametre bir derlemeyi `pbIsFrameworkAssembly` Isimlendirilemez, Boolean değeri içerir `false` .</span><span class="sxs-lookup"><span data-stu-id="f5f7c-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5f7c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5f7c-114">Requirements</span></span>  

 <span data-ttu-id="f5f7c-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5f7c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5f7c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5f7c-116">See also</span></span>

- [<span data-ttu-id="f5f7c-117">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f5f7c-117">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
