---
title: CloseEnum Yöntemi
ms.date: 03/30/2017
api_name:
- CloseEnum
- IALink.CloseEnum
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseEnum
helpviewer_keywords:
- CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 145f92badf39b6456a82df8f7de23f1784d2ce50
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495747"
---
# <a name="closeenum-method"></a><span data-ttu-id="61876-102">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61876-102">CloseEnum Method</span></span>
<span data-ttu-id="61876-103">Belirtilen numaralandırma kapatır ve ilişkili kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="61876-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61876-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61876-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="61876-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61876-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="61876-106">Kapatılan numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="61876-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61876-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="61876-107">Return Value</span></span>  
 <span data-ttu-id="61876-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="61876-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61876-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61876-109">Requirements</span></span>  
 <span data-ttu-id="61876-110">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="61876-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61876-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61876-111">See also</span></span>
- [<span data-ttu-id="61876-112">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61876-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="61876-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61876-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="61876-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="61876-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
