---
title: "IsFrameworkAssembly İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IsFrameworkAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IsFrameworkAssembly
helpviewer_keywords: IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa077ce13031772ec2ea20708c1dbd29da02d32a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="28c8a-102">IsFrameworkAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="28c8a-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="28c8a-103">Belirtilen derleme yönetilen olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="28c8a-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28c8a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28c8a-104">Syntax</span></span>  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28c8a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28c8a-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="28c8a-106">[in] Denetlenecek derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="28c8a-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="28c8a-107">[out] Derleme yönetilen olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="28c8a-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="28c8a-108">[in] Derleme benzersiz kimliğini içeren bir uncanonicalized dize.</span><span class="sxs-lookup"><span data-stu-id="28c8a-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="28c8a-109">[in] Boyutunu `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="28c8a-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28c8a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28c8a-110">Remarks</span></span>  
 <span data-ttu-id="28c8a-111">`pwzAssemblyReference` Bir işaretçi bir derleme adını içeren bir karakter dizesi parametresidir.</span><span class="sxs-lookup"><span data-stu-id="28c8a-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="28c8a-112">Bu derleme parçasıysa .NET Framework'ün `pbIsFrameworkAssembly` parametre bir Boole değeri içerecek `true`.</span><span class="sxs-lookup"><span data-stu-id="28c8a-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="28c8a-113">Adlandırılmış derlemesi .NET Framework'ün bir parçası değilse veya `pwzAssemblyReference` parametre bir derleme adı değil `pbIsFrameworkAssembly` bir Boole değeri içerecektir `false`.</span><span class="sxs-lookup"><span data-stu-id="28c8a-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28c8a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28c8a-114">Requirements</span></span>  
 <span data-ttu-id="28c8a-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28c8a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28c8a-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28c8a-116">See Also</span></span>  
 [<span data-ttu-id="28c8a-117">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="28c8a-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
