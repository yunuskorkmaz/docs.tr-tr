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
ms.openlocfilehash: 216a7221550cb6345b29b5ed9e45b13ce40eadf4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="f0ff7-102">IsFrameworkAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="f0ff7-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="f0ff7-103">Belirtilen derleme yönetilen olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f0ff7-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0ff7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0ff7-104">Syntax</span></span>  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0ff7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0ff7-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="f0ff7-106">[in] Denetlenecek derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="f0ff7-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="f0ff7-107">[out] Derleme yönetilen olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f0ff7-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="f0ff7-108">[in] Derleme benzersiz kimliğini içeren bir uncanonicalized dize.</span><span class="sxs-lookup"><span data-stu-id="f0ff7-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="f0ff7-109">[in] Boyutunu `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="f0ff7-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0ff7-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0ff7-110">Remarks</span></span>  
 <span data-ttu-id="f0ff7-111">`pwzAssemblyReference` Bir işaretçi bir derleme adını içeren bir karakter dizesi parametresidir.</span><span class="sxs-lookup"><span data-stu-id="f0ff7-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="f0ff7-112">Bu derleme parçasıysa .NET Framework'ün `pbIsFrameworkAssembly` parametre bir Boole değeri içerecek `true`.</span><span class="sxs-lookup"><span data-stu-id="f0ff7-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="f0ff7-113">Adlandırılmış derlemesi .NET Framework'ün bir parçası değilse veya `pwzAssemblyReference` parametre bir derleme adı değil `pbIsFrameworkAssembly` bir Boole değeri içerecektir `false`.</span><span class="sxs-lookup"><span data-stu-id="f0ff7-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0ff7-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0ff7-114">Requirements</span></span>  
 <span data-ttu-id="f0ff7-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0ff7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ff7-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0ff7-116">See Also</span></span>  
 [<span data-ttu-id="f0ff7-117">Fusion genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="f0ff7-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
