---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2bfb43002b79fd3e499272b87756bdc3ab0b589
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787332"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="e4841-102">GetResolutionScope Metodu</span><span class="sxs-lookup"><span data-stu-id="e4841-102">GetResolutionScope Method</span></span>
<span data-ttu-id="e4841-103">Verilen bir türün kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="e4841-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4841-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4841-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4841-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4841-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e4841-106">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e4841-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e4841-107">Bir başvuru gerektiren dosya.</span><span class="sxs-lookup"><span data-stu-id="e4841-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="e4841-108">Türü tanımlanmış, genellikle [ImportFile yöntemiyle](importfile-method.md)alınan dosyanın belirteci.</span><span class="sxs-lookup"><span data-stu-id="e4841-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="e4841-109">Derlemeyi veya modül başvurusunu alır.</span><span class="sxs-lookup"><span data-stu-id="e4841-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4841-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e4841-110">Return Value</span></span>  
 <span data-ttu-id="e4841-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4841-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4841-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4841-112">Requirements</span></span>  
 <span data-ttu-id="e4841-113">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e4841-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4841-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4841-114">See also</span></span>

- [<span data-ttu-id="e4841-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4841-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e4841-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4841-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e4841-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="e4841-117">ALink API</span></span>](index.md)
