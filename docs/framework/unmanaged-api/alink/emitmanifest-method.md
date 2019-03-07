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
ms.openlocfilehash: 28be714a70229b8a4628db2efff0dc2d890e231b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485505"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="6c2c1-102">EmitManifest Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c2c1-102">EmitManifest Method</span></span>
<span data-ttu-id="6c2c1-103">Son bildirim yayar.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-103">Emits the final manifest.</span></span> <span data-ttu-id="6c2c1-104">Diğer tüm dosyalar ve tüm ayarları sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="6c2c1-105">İlişkisiz modüller için bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c2c1-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c2c1-106">Syntax</span></span>  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c2c1-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c2c1-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6c2c1-108">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="6c2c1-109">Alınan derleme dosyasında ayrılacak boyutu alır [StrongNameSignatureSize işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="6c2c1-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="6c2c1-110">İsteğe bağlı olarak, derleme bildirimi belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c2c1-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6c2c1-111">Return Value</span></span>  
 <span data-ttu-id="6c2c1-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c2c1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c2c1-113">Requirements</span></span>  
 <span data-ttu-id="6c2c1-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c2c1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c2c1-115">See also</span></span>
- [<span data-ttu-id="6c2c1-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c2c1-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="6c2c1-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c2c1-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="6c2c1-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="6c2c1-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
