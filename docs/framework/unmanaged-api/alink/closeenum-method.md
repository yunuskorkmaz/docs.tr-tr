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
ms.openlocfilehash: 8d9529022eb04c81152dced5c63f255c510851a0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777467"
---
# <a name="closeenum-method"></a><span data-ttu-id="4d778-102">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d778-102">CloseEnum Method</span></span>
<span data-ttu-id="4d778-103">Belirtilen numaralandırmayı kapatır ve ilişkili kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="4d778-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d778-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d778-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d778-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4d778-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="4d778-106">Kapatılacak numaralandırmanın tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="4d778-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d778-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4d778-107">Return Value</span></span>  
 <span data-ttu-id="4d778-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="4d778-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d778-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d778-109">Requirements</span></span>  
 <span data-ttu-id="4d778-110">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="4d778-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d778-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d778-111">See also</span></span>

- [<span data-ttu-id="4d778-112">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d778-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4d778-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d778-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4d778-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="4d778-114">ALink API</span></span>](index.md)
