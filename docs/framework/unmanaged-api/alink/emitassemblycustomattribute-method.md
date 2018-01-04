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
ms.workload: dotnet
ms.openlocfilehash: 9cc7709ef060642f12a8bc7d048e520427a5c674
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="b7a81-102">EmitAssemblyCustomAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7a81-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="b7a81-103">Derleme düzeyi özel öznitelikleri ayarlamak için çağırın.</span><span class="sxs-lookup"><span data-stu-id="b7a81-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7a81-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7a81-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="b7a81-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7a81-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b7a81-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="b7a81-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="b7a81-107">Öznitelik defiles dosyası.</span><span class="sxs-lookup"><span data-stu-id="b7a81-107">File that defiles the attribute.</span></span> <span data-ttu-id="b7a81-108">NULL olabilir `AssemblyID` ilişkisiz netmodule göstermez.</span><span class="sxs-lookup"><span data-stu-id="b7a81-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="b7a81-109">Özel öznitelik türü.</span><span class="sxs-lookup"><span data-stu-id="b7a81-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="b7a81-110">Özel değer verisi.</span><span class="sxs-lookup"><span data-stu-id="b7a81-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="b7a81-111">Özel değer verisi uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="b7a81-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="b7a81-112">Özel öznitelik derleme imzalama ilişkiliyse TRUE.</span><span class="sxs-lookup"><span data-stu-id="b7a81-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="b7a81-113">Birden çok öznitelik yayınlaması gerekiyorsa TRUE.</span><span class="sxs-lookup"><span data-stu-id="b7a81-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7a81-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b7a81-114">Return Value</span></span>  
 <span data-ttu-id="b7a81-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="b7a81-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7a81-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7a81-116">Requirements</span></span>  
 <span data-ttu-id="b7a81-117">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="b7a81-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7a81-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7a81-118">See Also</span></span>  
 [<span data-ttu-id="b7a81-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7a81-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="b7a81-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7a81-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="b7a81-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="b7a81-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
