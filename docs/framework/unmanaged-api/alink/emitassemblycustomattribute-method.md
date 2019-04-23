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
ms.openlocfilehash: 67073f04cfe981dd383369029d9a4b436929a0a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117851"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="7f63d-102">EmitAssemblyCustomAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f63d-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="7f63d-103">Özel derleme düzeyinde öznitelikler ayarlanacak çağırın.</span><span class="sxs-lookup"><span data-stu-id="7f63d-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f63d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f63d-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7f63d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f63d-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7f63d-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="7f63d-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="7f63d-107">Öznitelik defiles dosyası.</span><span class="sxs-lookup"><span data-stu-id="7f63d-107">File that defiles the attribute.</span></span> <span data-ttu-id="7f63d-108">NULL olabilir `AssemblyID` ilişkisiz bir netmodule göstermez.</span><span class="sxs-lookup"><span data-stu-id="7f63d-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="7f63d-109">Özel özniteliğin türü.</span><span class="sxs-lookup"><span data-stu-id="7f63d-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="7f63d-110">Özel değer verileri.</span><span class="sxs-lookup"><span data-stu-id="7f63d-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="7f63d-111">Özel değer verisi uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="7f63d-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="7f63d-112">Derleme imzalama için özel özniteliği ilişkiliyse TRUE.</span><span class="sxs-lookup"><span data-stu-id="7f63d-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="7f63d-113">Birden çok öznitelik yayılan gerekiyorsa TRUE.</span><span class="sxs-lookup"><span data-stu-id="7f63d-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f63d-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7f63d-114">Return Value</span></span>  
 <span data-ttu-id="7f63d-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="7f63d-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f63d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f63d-116">Requirements</span></span>  
 <span data-ttu-id="7f63d-117">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="7f63d-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f63d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f63d-118">See also</span></span>

- [<span data-ttu-id="7f63d-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f63d-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="7f63d-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f63d-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="7f63d-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="7f63d-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
