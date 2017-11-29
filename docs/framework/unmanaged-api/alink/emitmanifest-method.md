---
title: "EmitManifest Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EmitManifest
- IALink.EmitManifest
api_location: alink.dll
api_type: COM
f1_keywords: EmitManifest
helpviewer_keywords: EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 03ef815f03a65cbf7e2dc936b21848e206132add
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="emitmanifest-method"></a><span data-ttu-id="682e8-102">EmitManifest Yöntemi</span><span class="sxs-lookup"><span data-stu-id="682e8-102">EmitManifest Method</span></span>
<span data-ttu-id="682e8-103">Son bildirim yayar.</span><span class="sxs-lookup"><span data-stu-id="682e8-103">Emits the final manifest.</span></span> <span data-ttu-id="682e8-104">Diğer tüm dosyaları alma ve tüm seçeneklerini ayarlama sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="682e8-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="682e8-105">İlişkisiz modülleri için bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="682e8-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="682e8-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="682e8-106">Syntax</span></span>  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="682e8-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="682e8-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="682e8-108">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="682e8-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="682e8-109">Kaynağından alınan derleme dosyasını ayrılacak boyutu alır [StrongNameSignatureSize işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="682e8-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="682e8-110">İsteğe bağlı olarak derleme bildirim belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="682e8-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="682e8-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="682e8-111">Return Value</span></span>  
 <span data-ttu-id="682e8-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="682e8-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="682e8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="682e8-113">Requirements</span></span>  
 <span data-ttu-id="682e8-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="682e8-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="682e8-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="682e8-115">See Also</span></span>  
 [<span data-ttu-id="682e8-116">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="682e8-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="682e8-117">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="682e8-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="682e8-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="682e8-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
