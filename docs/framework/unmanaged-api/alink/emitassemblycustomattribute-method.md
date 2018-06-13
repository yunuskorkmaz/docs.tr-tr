---
title: EmitAssemblyCustomAttribute Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: daf2c3dcaf16e949f8770121d8324cbfe6c7d05b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404085"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="a42b9-102">EmitAssemblyCustomAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a42b9-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="a42b9-103">Derleme düzeyi özel öznitelikleri ayarlamak için çağırın.</span><span class="sxs-lookup"><span data-stu-id="a42b9-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a42b9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a42b9-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="a42b9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a42b9-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a42b9-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="a42b9-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="a42b9-107">Öznitelik defiles dosyası.</span><span class="sxs-lookup"><span data-stu-id="a42b9-107">File that defiles the attribute.</span></span> <span data-ttu-id="a42b9-108">NULL olabilir `AssemblyID` ilişkisiz netmodule göstermez.</span><span class="sxs-lookup"><span data-stu-id="a42b9-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="a42b9-109">Özel öznitelik türü.</span><span class="sxs-lookup"><span data-stu-id="a42b9-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="a42b9-110">Özel değer verisi.</span><span class="sxs-lookup"><span data-stu-id="a42b9-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="a42b9-111">Özel değer verisi uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="a42b9-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="a42b9-112">Özel öznitelik derleme imzalama ilişkiliyse TRUE.</span><span class="sxs-lookup"><span data-stu-id="a42b9-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="a42b9-113">Birden çok öznitelik yayınlaması gerekiyorsa TRUE.</span><span class="sxs-lookup"><span data-stu-id="a42b9-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a42b9-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a42b9-114">Return Value</span></span>  
 <span data-ttu-id="a42b9-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="a42b9-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a42b9-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a42b9-116">Requirements</span></span>  
 <span data-ttu-id="a42b9-117">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="a42b9-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a42b9-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a42b9-118">See Also</span></span>  
 [<span data-ttu-id="a42b9-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a42b9-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="a42b9-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a42b9-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="a42b9-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="a42b9-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
