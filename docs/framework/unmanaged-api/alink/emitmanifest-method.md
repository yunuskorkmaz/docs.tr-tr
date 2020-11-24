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
ms.openlocfilehash: b1c005e58f18b03a7da5f3836f719b95c41bca95
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684947"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="31388-102">EmitManifest Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31388-102">EmitManifest Method</span></span>

<span data-ttu-id="31388-103">Son bildirimi yayar.</span><span class="sxs-lookup"><span data-stu-id="31388-103">Emits the final manifest.</span></span> <span data-ttu-id="31388-104">Diğer tüm dosyaları içeri aktardıktan sonra ve tüm seçenekleri ayarlayarak bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="31388-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="31388-105">İlişkisiz modüller için bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="31388-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31388-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="31388-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="31388-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31388-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="31388-108">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="31388-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="31388-109">[Strongnametabeturesize işlevinden](../strong-naming/strongnamesignaturesize-function.md)alınan derleme dosyasında ayrılacak boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="31388-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="31388-110">İsteğe bağlı olarak, derleme bildirimi belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="31388-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31388-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="31388-111">Return Value</span></span>  

 <span data-ttu-id="31388-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="31388-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31388-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31388-113">Requirements</span></span>  

 <span data-ttu-id="31388-114">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="31388-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31388-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31388-115">See also</span></span>

- [<span data-ttu-id="31388-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31388-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="31388-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31388-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="31388-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="31388-118">ALink API</span></span>](index.md)
