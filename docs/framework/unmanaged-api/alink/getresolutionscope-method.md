---
title: GetResolutionScope Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetResolutionScope
api_location: alink.dll
api_type: COM
f1_keywords: GetResolutionScope
helpviewer_keywords: GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 11ccbce4d8e9783514050f6b41c6e32cde6c274f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="3ecc1-102">GetResolutionScope Metodu</span><span class="sxs-lookup"><span data-stu-id="3ecc1-102">GetResolutionScope Method</span></span>
<span data-ttu-id="3ecc1-103">Belirli bir türde kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="3ecc1-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ecc1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ecc1-104">Syntax</span></span>  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ecc1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3ecc1-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3ecc1-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="3ecc1-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3ecc1-107">Gerekli bir başvuru dosyası.</span><span class="sxs-lookup"><span data-stu-id="3ecc1-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="3ecc1-108">Belirteç dosyasının bu türü ile genellikle alınan tanımlı [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="3ecc1-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="3ecc1-109">Derleme veya modül başvurusu alır.</span><span class="sxs-lookup"><span data-stu-id="3ecc1-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ecc1-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3ecc1-110">Return Value</span></span>  
 <span data-ttu-id="3ecc1-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ecc1-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ecc1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ecc1-112">Requirements</span></span>  
 <span data-ttu-id="3ecc1-113">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3ecc1-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ecc1-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ecc1-114">See Also</span></span>  
 [<span data-ttu-id="3ecc1-115">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ecc1-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="3ecc1-116">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ecc1-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="3ecc1-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="3ecc1-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
