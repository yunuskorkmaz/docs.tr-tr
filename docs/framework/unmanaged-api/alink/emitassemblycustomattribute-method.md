---
title: "EmitAssemblyCustomAttribute Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location: alink.dll
api_type: COM
f1_keywords: EmitAssemblyCustomAttribute
helpviewer_keywords: EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bb21ee1396a9dd0426b9b91711c2345ef66c09f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="84b0a-102">EmitAssemblyCustomAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84b0a-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="84b0a-103">Derleme düzeyi özel öznitelikleri ayarlamak için çağırın.</span><span class="sxs-lookup"><span data-stu-id="84b0a-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84b0a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84b0a-104">Syntax</span></span>  
  
```  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84b0a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84b0a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="84b0a-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="84b0a-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="84b0a-107">Öznitelik defiles dosyası.</span><span class="sxs-lookup"><span data-stu-id="84b0a-107">File that defiles the attribute.</span></span> <span data-ttu-id="84b0a-108">NULL olabilir `AssemblyID` ilişkisiz netmodule göstermez.</span><span class="sxs-lookup"><span data-stu-id="84b0a-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="84b0a-109">Özel öznitelik türü.</span><span class="sxs-lookup"><span data-stu-id="84b0a-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="84b0a-110">Özel değer verisi.</span><span class="sxs-lookup"><span data-stu-id="84b0a-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="84b0a-111">Özel değer verisi uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="84b0a-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="84b0a-112">Özel öznitelik derleme imzalama ilişkiliyse TRUE.</span><span class="sxs-lookup"><span data-stu-id="84b0a-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="84b0a-113">Birden çok öznitelik yayınlaması gerekiyorsa TRUE.</span><span class="sxs-lookup"><span data-stu-id="84b0a-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84b0a-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="84b0a-114">Return Value</span></span>  
 <span data-ttu-id="84b0a-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="84b0a-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84b0a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84b0a-116">Requirements</span></span>  
 <span data-ttu-id="84b0a-117">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="84b0a-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b0a-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84b0a-118">See Also</span></span>  
 [<span data-ttu-id="84b0a-119">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="84b0a-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="84b0a-120">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="84b0a-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="84b0a-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="84b0a-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
