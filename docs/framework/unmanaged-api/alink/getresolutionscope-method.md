---
description: 'Daha fazla bilgi edinin: GetResolutionScope Yöntemi'
title: GetResolutionScope Metodu
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
ms.openlocfilehash: add8ccb1ef6eb0f4b688dcf80563e9280099120d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718401"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="25757-103">GetResolutionScope Metodu</span><span class="sxs-lookup"><span data-stu-id="25757-103">GetResolutionScope Method</span></span>

<span data-ttu-id="25757-104">Verilen bir türün kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="25757-104">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25757-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25757-105">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="25757-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25757-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="25757-107">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="25757-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="25757-108">Bir başvuru gerektiren dosya.</span><span class="sxs-lookup"><span data-stu-id="25757-108">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="25757-109">Türü tanımlanmış, genellikle [ImportFile yöntemiyle](importfile-method.md)alınan dosyanın belirteci.</span><span class="sxs-lookup"><span data-stu-id="25757-109">Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="25757-110">Derlemeyi veya modül başvurusunu alır.</span><span class="sxs-lookup"><span data-stu-id="25757-110">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25757-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="25757-111">Return Value</span></span>  

 <span data-ttu-id="25757-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="25757-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25757-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25757-113">Requirements</span></span>  

 <span data-ttu-id="25757-114">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="25757-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25757-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25757-115">See also</span></span>

- [<span data-ttu-id="25757-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25757-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="25757-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25757-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="25757-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="25757-118">ALink API</span></span>](index.md)
