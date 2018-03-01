---
title: GetResolutionScope Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f9dc63a7165ab472e973e0bc4f3e4cbb99e5d828
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="c7b07-102">GetResolutionScope Metodu</span><span class="sxs-lookup"><span data-stu-id="c7b07-102">GetResolutionScope Method</span></span>
<span data-ttu-id="c7b07-103">Belirli bir türde kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="c7b07-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7b07-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7b07-104">Syntax</span></span>  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7b07-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7b07-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c7b07-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="c7b07-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c7b07-107">Gerekli bir başvuru dosyası.</span><span class="sxs-lookup"><span data-stu-id="c7b07-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="c7b07-108">Belirteç dosyasının bu türü ile genellikle alınan tanımlı [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="c7b07-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="c7b07-109">Derleme veya modül başvurusu alır.</span><span class="sxs-lookup"><span data-stu-id="c7b07-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7b07-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c7b07-110">Return Value</span></span>  
 <span data-ttu-id="c7b07-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7b07-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7b07-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7b07-112">Requirements</span></span>  
 <span data-ttu-id="c7b07-113">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c7b07-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7b07-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7b07-114">See Also</span></span>  
 [<span data-ttu-id="c7b07-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7b07-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c7b07-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7b07-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c7b07-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="c7b07-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
