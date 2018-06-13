---
title: EmitManifest Yöntemi
ms.date: 03/30/2017
api_name:
- EmitManifest
- IALink.EmitManifest
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitManifest
helpviewer_keywords:
- EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6df28cd3eaadfe62cd34e20e6e03d5a89e6bb425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401215"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="7b92b-102">EmitManifest Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b92b-102">EmitManifest Method</span></span>
<span data-ttu-id="7b92b-103">Son bildirim yayar.</span><span class="sxs-lookup"><span data-stu-id="7b92b-103">Emits the final manifest.</span></span> <span data-ttu-id="7b92b-104">Diğer tüm dosyaları alma ve tüm seçeneklerini ayarlama sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="7b92b-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="7b92b-105">İlişkisiz modülleri için bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7b92b-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b92b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b92b-106">Syntax</span></span>  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b92b-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7b92b-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7b92b-108">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="7b92b-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="7b92b-109">Kaynağından alınan derleme dosyasını ayrılacak boyutu alır [StrongNameSignatureSize işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="7b92b-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="7b92b-110">İsteğe bağlı olarak derleme bildirim belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="7b92b-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b92b-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7b92b-111">Return Value</span></span>  
 <span data-ttu-id="7b92b-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b92b-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b92b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b92b-113">Requirements</span></span>  
 <span data-ttu-id="7b92b-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7b92b-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b92b-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b92b-115">See Also</span></span>  
 [<span data-ttu-id="7b92b-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b92b-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7b92b-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b92b-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="7b92b-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="7b92b-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
