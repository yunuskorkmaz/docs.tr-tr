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
ms.openlocfilehash: 91dc4cb7d64d49d1e95c0c8eb79a29736559d842
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742091"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="78b35-102">EmitManifest Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78b35-102">EmitManifest Method</span></span>
<span data-ttu-id="78b35-103">Son bildirim yayar.</span><span class="sxs-lookup"><span data-stu-id="78b35-103">Emits the final manifest.</span></span> <span data-ttu-id="78b35-104">Diğer tüm dosyalar ve tüm ayarları sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="78b35-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="78b35-105">İlişkisiz modüller için bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="78b35-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78b35-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78b35-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="78b35-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="78b35-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="78b35-108">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="78b35-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="78b35-109">Alınan derleme dosyasında ayrılacak boyutu alır [StrongNameSignatureSize işlevi](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="78b35-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="78b35-110">İsteğe bağlı olarak, derleme bildirimi belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="78b35-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78b35-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="78b35-111">Return Value</span></span>  
 <span data-ttu-id="78b35-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="78b35-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78b35-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78b35-113">Requirements</span></span>  
 <span data-ttu-id="78b35-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="78b35-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78b35-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78b35-115">See also</span></span>

- [<span data-ttu-id="78b35-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78b35-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="78b35-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78b35-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="78b35-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="78b35-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
