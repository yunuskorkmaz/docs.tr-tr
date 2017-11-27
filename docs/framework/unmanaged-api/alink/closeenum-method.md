---
title: "CloseEnum Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CloseEnum
- IALink.CloseEnum
api_location: alink.dll
api_type: COM
f1_keywords: CloseEnum
helpviewer_keywords: CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6ade939969069fb35221d83f8c7e4e380e903a00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="closeenum-method"></a><span data-ttu-id="377d5-102">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="377d5-102">CloseEnum Method</span></span>
<span data-ttu-id="377d5-103">Belirtilen numaralandırma kapatır ve ilişkili kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="377d5-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="377d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="377d5-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="377d5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="377d5-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="377d5-106">Kapatılması için numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="377d5-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="377d5-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="377d5-107">Return Value</span></span>  
 <span data-ttu-id="377d5-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="377d5-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="377d5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="377d5-109">Requirements</span></span>  
 <span data-ttu-id="377d5-110">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="377d5-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="377d5-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="377d5-111">See Also</span></span>  
 [<span data-ttu-id="377d5-112">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="377d5-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="377d5-113">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="377d5-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="377d5-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="377d5-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
