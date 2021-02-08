---
description: 'Daha fazla bilgi edinin: IsFrameworkAssembly Işlevi'
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
ms.openlocfilehash: 8f264df7b1ae5c494298b11ebd94cc93aed5543a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800025"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="5fbd9-103">IsFrameworkAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="5fbd9-103">IsFrameworkAssembly Function</span></span>

<span data-ttu-id="5fbd9-104">Belirtilen derlemenin yönetilip yönetilmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="5fbd9-104">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fbd9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fbd9-105">Syntax</span></span>  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fbd9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5fbd9-106">Parameters</span></span>  

 `pwzAssemblyReference`  
 <span data-ttu-id="5fbd9-107">'ndaki Denetlenecek derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="5fbd9-107">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="5fbd9-108">dışı Derlemenin yönetilip yönetilmediğini gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="5fbd9-108">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="5fbd9-109">'ndaki Derlemenin benzersiz kimliğini içeren bir Uncanonicalized dizesi.</span><span class="sxs-lookup"><span data-stu-id="5fbd9-109">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="5fbd9-110">'ndaki Boyutu `pwzFrameworkAssemblyIdentity` .</span><span class="sxs-lookup"><span data-stu-id="5fbd9-110">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fbd9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5fbd9-111">Remarks</span></span>  

 <span data-ttu-id="5fbd9-112">Parametresi, bir `pwzAssemblyReference` derlemenin adını içeren bir karakter dizesinin bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="5fbd9-112">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="5fbd9-113">Bu derleme .NET Framework bir parçasıysa, `pbIsFrameworkAssembly` parametresi bir Boolean değeri içerir `true` .</span><span class="sxs-lookup"><span data-stu-id="5fbd9-113">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="5fbd9-114">Adlandırılmış derleme .NET Framework bir parçası değilse veya `pwzAssemblyReference` parametre bir derlemeyi `pbIsFrameworkAssembly` Isimlendirilemez, Boolean değeri içerir `false` .</span><span class="sxs-lookup"><span data-stu-id="5fbd9-114">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fbd9-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5fbd9-115">Requirements</span></span>  

 <span data-ttu-id="5fbd9-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fbd9-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fbd9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fbd9-117">See also</span></span>

- [<span data-ttu-id="5fbd9-118">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5fbd9-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
