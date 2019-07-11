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
ms.openlocfilehash: c6c2e741df594e265fdef51a602a9a4927733b7c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741870"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="c8add-102">GetResolutionScope Metodu</span><span class="sxs-lookup"><span data-stu-id="c8add-102">GetResolutionScope Method</span></span>
<span data-ttu-id="c8add-103">Kapsamı belirli bir türden alır.</span><span class="sxs-lookup"><span data-stu-id="c8add-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8add-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8add-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8add-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8add-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c8add-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="c8add-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c8add-107">Geçirilmesi gereken başvuru dosya.</span><span class="sxs-lookup"><span data-stu-id="c8add-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="c8add-108">Dosyanın belirteç türü, genellikle alınan tanımlanan [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="c8add-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="c8add-109">Derleme veya modül başvurusu alır.</span><span class="sxs-lookup"><span data-stu-id="c8add-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8add-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c8add-110">Return Value</span></span>  
 <span data-ttu-id="c8add-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="c8add-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8add-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8add-112">Requirements</span></span>  
 <span data-ttu-id="c8add-113">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c8add-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8add-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8add-114">See also</span></span>

- [<span data-ttu-id="c8add-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8add-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c8add-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8add-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c8add-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="c8add-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
