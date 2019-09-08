---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4cf862ae3676b85a7fc3f09a4f5794e01284737
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787229"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="8ff58-102">PreCloseAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ff58-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="8ff58-103">Derleme dosyasını kapatır.</span><span class="sxs-lookup"><span data-stu-id="8ff58-103">Closes the assembly file.</span></span> <span data-ttu-id="8ff58-104">Diğer tüm dosyaları kapattıktan sonra, ancak derleme dosyasını kapatmadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="8ff58-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="8ff58-105">İlişkisiz modüller için bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="8ff58-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff58-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ff58-106">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ff58-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ff58-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8ff58-108">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="8ff58-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ff58-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8ff58-109">Return Value</span></span>  
 <span data-ttu-id="8ff58-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ff58-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ff58-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ff58-111">Requirements</span></span>  
 <span data-ttu-id="8ff58-112">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8ff58-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff58-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ff58-113">See also</span></span>

- [<span data-ttu-id="8ff58-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ff58-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8ff58-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ff58-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8ff58-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="8ff58-116">ALink API</span></span>](index.md)
