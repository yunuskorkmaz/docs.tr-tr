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
ms.openlocfilehash: e1aeffbd5d5b22bea87dd7a49a3268822ce84d38
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481192"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="2c14c-102">PreCloseAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c14c-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="2c14c-103">Derleme dosyası kapatır.</span><span class="sxs-lookup"><span data-stu-id="2c14c-103">Closes the assembly file.</span></span> <span data-ttu-id="2c14c-104">Diğer tüm dosyalar kapatıldıktan sonra ancak derleme dosyasını kapatmadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="2c14c-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="2c14c-105">İlişkisiz modüller için bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2c14c-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c14c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c14c-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c14c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c14c-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2c14c-108">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="2c14c-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c14c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2c14c-109">Return Value</span></span>  
 <span data-ttu-id="2c14c-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="2c14c-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c14c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c14c-111">Requirements</span></span>  
 <span data-ttu-id="2c14c-112">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2c14c-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c14c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c14c-113">See also</span></span>
- [<span data-ttu-id="2c14c-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c14c-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="2c14c-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c14c-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="2c14c-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="2c14c-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
