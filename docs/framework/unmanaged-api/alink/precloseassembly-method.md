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
ms.openlocfilehash: aab42e939651d75b1933962d72ba8bec1090f52d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184515"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="ddc0e-102">PreCloseAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ddc0e-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="ddc0e-103">Derleme dosyası kapatır.</span><span class="sxs-lookup"><span data-stu-id="ddc0e-103">Closes the assembly file.</span></span> <span data-ttu-id="ddc0e-104">Diğer tüm dosyalar kapatıldıktan sonra ancak derleme dosyasını kapatmadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="ddc0e-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="ddc0e-105">İlişkisiz modüller için bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ddc0e-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddc0e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ddc0e-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddc0e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ddc0e-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ddc0e-108">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="ddc0e-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddc0e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ddc0e-109">Return Value</span></span>  
 <span data-ttu-id="ddc0e-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="ddc0e-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddc0e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ddc0e-111">Requirements</span></span>  
 <span data-ttu-id="ddc0e-112">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ddc0e-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddc0e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddc0e-113">See also</span></span>

- [<span data-ttu-id="ddc0e-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ddc0e-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="ddc0e-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ddc0e-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="ddc0e-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="ddc0e-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
