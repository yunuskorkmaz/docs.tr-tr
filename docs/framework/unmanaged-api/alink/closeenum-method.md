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
ms.openlocfilehash: e5c3185dc6d488223d5882f543f0c690d82261b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402450"
---
# <a name="closeenum-method"></a><span data-ttu-id="b7826-102">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7826-102">CloseEnum Method</span></span>
<span data-ttu-id="b7826-103">Belirtilen numaralandırma kapatır ve ilişkili kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="b7826-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7826-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7826-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7826-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7826-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="b7826-106">Kapatılması için numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="b7826-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7826-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b7826-107">Return Value</span></span>  
 <span data-ttu-id="b7826-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="b7826-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7826-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7826-109">Requirements</span></span>  
 <span data-ttu-id="b7826-110">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="b7826-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7826-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7826-111">See Also</span></span>  
 [<span data-ttu-id="b7826-112">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7826-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="b7826-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7826-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="b7826-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="b7826-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
