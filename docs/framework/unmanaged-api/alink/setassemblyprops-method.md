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
ms.workload: dotnet
ms.openlocfilehash: ae13daab0352ad4367c7ad6e06d6c12af23c75bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="30bcb-102">SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30bcb-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="30bcb-103">Derleme düzeyinde özellikler atar.</span><span class="sxs-lookup"><span data-stu-id="30bcb-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30bcb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30bcb-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30bcb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30bcb-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="30bcb-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="30bcb-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="30bcb-107">Özelliği tanımlar dosyası.</span><span class="sxs-lookup"><span data-stu-id="30bcb-107">File that defines the property.</span></span> <span data-ttu-id="30bcb-108">NULL olabilir `AssemblyID` ilişkisiz netmodule göstermez.</span><span class="sxs-lookup"><span data-stu-id="30bcb-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="30bcb-109">Değiştirme seçeneğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="30bcb-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="30bcb-110">Seçeneği yeni değeri.</span><span class="sxs-lookup"><span data-stu-id="30bcb-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30bcb-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="30bcb-111">Return Value</span></span>  
 <span data-ttu-id="30bcb-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="30bcb-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30bcb-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30bcb-113">Requirements</span></span>  
 <span data-ttu-id="30bcb-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="30bcb-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30bcb-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30bcb-115">See Also</span></span>  
 [<span data-ttu-id="30bcb-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30bcb-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="30bcb-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30bcb-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="30bcb-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="30bcb-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
