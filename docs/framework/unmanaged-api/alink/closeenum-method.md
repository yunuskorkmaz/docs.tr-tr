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
ms.openlocfilehash: 9b6c839cc664105149f26b0d21d7ba7fb91b3e29
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742206"
---
# <a name="closeenum-method"></a><span data-ttu-id="d0c6f-102">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0c6f-102">CloseEnum Method</span></span>
<span data-ttu-id="d0c6f-103">Belirtilen numaralandırma kapatır ve ilişkili kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="d0c6f-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0c6f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0c6f-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0c6f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0c6f-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="d0c6f-106">Kapatılan numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="d0c6f-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0c6f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d0c6f-107">Return Value</span></span>  
 <span data-ttu-id="d0c6f-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0c6f-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0c6f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0c6f-109">Requirements</span></span>  
 <span data-ttu-id="d0c6f-110">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="d0c6f-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0c6f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0c6f-111">See also</span></span>

- [<span data-ttu-id="d0c6f-112">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0c6f-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="d0c6f-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0c6f-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="d0c6f-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="d0c6f-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
