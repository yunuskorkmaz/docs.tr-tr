---
description: 'Daha fazla bilgi edinin: EmitManifest yöntemi'
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
ms.openlocfilehash: 770631864c030c067feb0b02d2f00c36076aa44c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638281"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="fcbcb-103">EmitManifest Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fcbcb-103">EmitManifest Method</span></span>

<span data-ttu-id="fcbcb-104">Son bildirimi yayar.</span><span class="sxs-lookup"><span data-stu-id="fcbcb-104">Emits the final manifest.</span></span> <span data-ttu-id="fcbcb-105">Diğer tüm dosyaları içeri aktardıktan sonra ve tüm seçenekleri ayarlayarak bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="fcbcb-105">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="fcbcb-106">İlişkisiz modüller için bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="fcbcb-106">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcbcb-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcbcb-107">Syntax</span></span>  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcbcb-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fcbcb-108">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="fcbcb-109">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="fcbcb-109">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="fcbcb-110">[Strongnametabeturesize işlevinden](../strong-naming/strongnamesignaturesize-function.md)alınan derleme dosyasında ayrılacak boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="fcbcb-110">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="fcbcb-111">İsteğe bağlı olarak, derleme bildirimi belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="fcbcb-111">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fcbcb-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fcbcb-112">Return Value</span></span>  

 <span data-ttu-id="fcbcb-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="fcbcb-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcbcb-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fcbcb-114">Requirements</span></span>  

 <span data-ttu-id="fcbcb-115">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fcbcb-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcbcb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcbcb-116">See also</span></span>

- [<span data-ttu-id="fcbcb-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcbcb-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="fcbcb-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcbcb-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="fcbcb-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="fcbcb-119">ALink API</span></span>](index.md)
