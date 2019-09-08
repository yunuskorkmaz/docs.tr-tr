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
ms.openlocfilehash: 77d54f6c8f67dda5132518d1fbd579a91ce82071
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777447"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="0f118-102">EmitAssemblyCustomAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f118-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="0f118-103">Derleme düzeyi özel özniteliklerini ayarlama çağrısı.</span><span class="sxs-lookup"><span data-stu-id="0f118-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f118-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f118-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0f118-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f118-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0f118-106">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0f118-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="0f118-107">Özniteliği olan dosyayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0f118-107">File that defiles the attribute.</span></span> <span data-ttu-id="0f118-108">İlişkisiz bir netmodule belirtmezse `AssemblyID` null olabilir.</span><span class="sxs-lookup"><span data-stu-id="0f118-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="0f118-109">Özel özniteliğin türü.</span><span class="sxs-lookup"><span data-stu-id="0f118-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="0f118-110">Özel değer verileri.</span><span class="sxs-lookup"><span data-stu-id="0f118-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="0f118-111">Özel değer verisinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="0f118-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="0f118-112">Özel öznitelik, derleme imzalama ile ilgiliyse TRUE.</span><span class="sxs-lookup"><span data-stu-id="0f118-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="0f118-113">Birden çok öznitelik yayınlandıysanız TRUE.</span><span class="sxs-lookup"><span data-stu-id="0f118-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f118-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0f118-114">Return Value</span></span>  
 <span data-ttu-id="0f118-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f118-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f118-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f118-116">Requirements</span></span>  
 <span data-ttu-id="0f118-117">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="0f118-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f118-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f118-118">See also</span></span>

- [<span data-ttu-id="0f118-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f118-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0f118-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f118-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0f118-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="0f118-121">ALink API</span></span>](index.md)
