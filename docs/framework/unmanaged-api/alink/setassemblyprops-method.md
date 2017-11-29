---
title: "SetAssemblyProps Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetAssemblyProps
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyProps
helpviewer_keywords: SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0245b6b1e30174bb3496d3d6ab674ccc00fb9fee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="aaa2a-102">SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aaa2a-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="aaa2a-103">Derleme düzeyinde özellikler atar.</span><span class="sxs-lookup"><span data-stu-id="aaa2a-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaa2a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aaa2a-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aaa2a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aaa2a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="aaa2a-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="aaa2a-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="aaa2a-107">Özelliği tanımlar dosyası.</span><span class="sxs-lookup"><span data-stu-id="aaa2a-107">File that defines the property.</span></span> <span data-ttu-id="aaa2a-108">NULL olabilir `AssemblyID` ilişkisiz netmodule göstermez.</span><span class="sxs-lookup"><span data-stu-id="aaa2a-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="aaa2a-109">Değiştirme seçeneğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="aaa2a-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="aaa2a-110">Seçeneği yeni değeri.</span><span class="sxs-lookup"><span data-stu-id="aaa2a-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aaa2a-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aaa2a-111">Return Value</span></span>  
 <span data-ttu-id="aaa2a-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="aaa2a-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaa2a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aaa2a-113">Requirements</span></span>  
 <span data-ttu-id="aaa2a-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="aaa2a-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa2a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aaa2a-115">See Also</span></span>  
 [<span data-ttu-id="aaa2a-116">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="aaa2a-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="aaa2a-117">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="aaa2a-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="aaa2a-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="aaa2a-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
