---
description: 'Şu konuda daha fazla bilgi edinin: Emıtassemblycustomattribute yöntemi'
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
ms.openlocfilehash: c91eb563c14b442a22db8f328287c10e5cc9a63c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638333"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="c551d-103">EmitAssemblyCustomAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c551d-103">EmitAssemblyCustomAttribute Method</span></span>

<span data-ttu-id="c551d-104">Derleme düzeyi özel özniteliklerini ayarlama çağrısı.</span><span class="sxs-lookup"><span data-stu-id="c551d-104">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c551d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c551d-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="c551d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c551d-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="c551d-107">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="c551d-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c551d-108">Özniteliği olan dosyayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c551d-108">File that defiles the attribute.</span></span> <span data-ttu-id="c551d-109">`AssemblyID`İlişkisiz bir netmodule BELIRTMEZSE null olabilir.</span><span class="sxs-lookup"><span data-stu-id="c551d-109">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="c551d-110">Özel özniteliğin türü.</span><span class="sxs-lookup"><span data-stu-id="c551d-110">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="c551d-111">Özel değer verileri.</span><span class="sxs-lookup"><span data-stu-id="c551d-111">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="c551d-112">Özel değer verisinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="c551d-112">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="c551d-113">Özel öznitelik, derleme imzalama ile ilgiliyse TRUE.</span><span class="sxs-lookup"><span data-stu-id="c551d-113">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="c551d-114">Birden çok öznitelik yayınlandıysanız TRUE.</span><span class="sxs-lookup"><span data-stu-id="c551d-114">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c551d-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c551d-115">Return Value</span></span>  

 <span data-ttu-id="c551d-116">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="c551d-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c551d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c551d-117">Requirements</span></span>  

 <span data-ttu-id="c551d-118">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="c551d-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c551d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c551d-119">See also</span></span>

- [<span data-ttu-id="c551d-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c551d-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c551d-121">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c551d-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c551d-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="c551d-122">ALink API</span></span>](index.md)
