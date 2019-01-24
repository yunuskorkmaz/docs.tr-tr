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
ms.openlocfilehash: 7b4909ae23d077ee079e062d0252dbf1ee11663c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538836"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="236be-102">EmitAssemblyCustomAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="236be-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="236be-103">Özel derleme düzeyinde öznitelikler ayarlanacak çağırın.</span><span class="sxs-lookup"><span data-stu-id="236be-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="236be-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="236be-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="236be-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="236be-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="236be-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="236be-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="236be-107">Öznitelik defiles dosyası.</span><span class="sxs-lookup"><span data-stu-id="236be-107">File that defiles the attribute.</span></span> <span data-ttu-id="236be-108">NULL olabilir `AssemblyID` ilişkisiz bir netmodule göstermez.</span><span class="sxs-lookup"><span data-stu-id="236be-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="236be-109">Özel özniteliğin türü.</span><span class="sxs-lookup"><span data-stu-id="236be-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="236be-110">Özel değer verileri.</span><span class="sxs-lookup"><span data-stu-id="236be-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="236be-111">Özel değer verisi uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="236be-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="236be-112">Derleme imzalama için özel özniteliği ilişkiliyse TRUE.</span><span class="sxs-lookup"><span data-stu-id="236be-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="236be-113">Birden çok öznitelik yayılan gerekiyorsa TRUE.</span><span class="sxs-lookup"><span data-stu-id="236be-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="236be-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="236be-114">Return Value</span></span>  
 <span data-ttu-id="236be-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="236be-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="236be-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="236be-116">Requirements</span></span>  
 <span data-ttu-id="236be-117">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="236be-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="236be-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="236be-118">See also</span></span>
- [<span data-ttu-id="236be-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="236be-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="236be-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="236be-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="236be-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="236be-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
