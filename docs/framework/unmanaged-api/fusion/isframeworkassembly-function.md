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
ms.openlocfilehash: 989d046bba1ba3170649e9d908a850bd1177fdd2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773837"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="1a471-102">IsFrameworkAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="1a471-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="1a471-103">Belirtilen derleme yönetilip yönetilmediğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="1a471-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a471-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a471-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a471-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a471-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="1a471-106">[in] Denetlenecek derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="1a471-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="1a471-107">[out] Derleme yönetilip yönetilmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="1a471-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="1a471-108">[in] Derlemenin benzersiz kimliği içeren uncanonicalized bir dize.</span><span class="sxs-lookup"><span data-stu-id="1a471-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="1a471-109">[in] Boyutu `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="1a471-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a471-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a471-110">Remarks</span></span>  
 <span data-ttu-id="1a471-111">`pwzAssemblyReference` Parametresi, bir derlemenin adını içeren bir karakter dizesine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1a471-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="1a471-112">Bu derleme parçasıysa .NET Framework'ün `pbIsFrameworkAssembly` parametresi bir Boolean değerini içerecek `true`.</span><span class="sxs-lookup"><span data-stu-id="1a471-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="1a471-113">Adlandırılmış derlemeyi .NET Framework'ün bir parçası değilse veya `pwzAssemblyReference` parametre, bir derleme adı değil `pbIsFrameworkAssembly` Boolean değerini içerecek `false`.</span><span class="sxs-lookup"><span data-stu-id="1a471-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a471-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a471-114">Requirements</span></span>  
 <span data-ttu-id="1a471-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a471-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a471-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a471-116">See also</span></span>

- [<span data-ttu-id="1a471-117">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1a471-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
