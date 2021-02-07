---
description: 'Daha fazla bilgi edinin: ön-Loseassembly yöntemi'
title: PreCloseAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
ms.openlocfilehash: 088a5bba654b3442da64672991d76537e9b4722c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662526"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="0007b-103">PreCloseAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0007b-103">PreCloseAssembly Method</span></span>

<span data-ttu-id="0007b-104">Derleme dosyasını kapatır.</span><span class="sxs-lookup"><span data-stu-id="0007b-104">Closes the assembly file.</span></span> <span data-ttu-id="0007b-105">Diğer tüm dosyaları kapattıktan sonra, ancak derleme dosyasını kapatmadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="0007b-105">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="0007b-106">İlişkisiz modüller için bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="0007b-106">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0007b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0007b-107">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0007b-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0007b-108">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="0007b-109">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0007b-109">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0007b-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0007b-110">Return Value</span></span>  

 <span data-ttu-id="0007b-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="0007b-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0007b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0007b-112">Requirements</span></span>  

 <span data-ttu-id="0007b-113">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0007b-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0007b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0007b-114">See also</span></span>

- [<span data-ttu-id="0007b-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0007b-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0007b-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0007b-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0007b-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="0007b-117">ALink API</span></span>](index.md)
