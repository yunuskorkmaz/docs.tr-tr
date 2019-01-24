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
ms.openlocfilehash: 009f7d20dfd6efc279b3187af8f5c95132ae51e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525241"
---
# <a name="closeenum-method"></a><span data-ttu-id="8e7d0-102">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e7d0-102">CloseEnum Method</span></span>
<span data-ttu-id="8e7d0-103">Belirtilen numaralandırma kapatır ve ilişkili kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="8e7d0-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e7d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e7d0-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e7d0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e7d0-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="8e7d0-106">Kapatılan numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="8e7d0-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e7d0-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8e7d0-107">Return Value</span></span>  
 <span data-ttu-id="8e7d0-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="8e7d0-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e7d0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e7d0-109">Requirements</span></span>  
 <span data-ttu-id="8e7d0-110">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="8e7d0-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e7d0-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e7d0-111">See also</span></span>
- [<span data-ttu-id="8e7d0-112">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e7d0-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="8e7d0-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e7d0-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="8e7d0-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="8e7d0-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
