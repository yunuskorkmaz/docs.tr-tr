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
ms.openlocfilehash: 59b1ec3f9ca382ef13680e3aad4d0c0c0e175f1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716973"
---
# <a name="closeenum-method"></a><span data-ttu-id="5d791-102">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d791-102">CloseEnum Method</span></span>

<span data-ttu-id="5d791-103">Belirtilen numaralandırmayı kapatır ve ilişkili kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="5d791-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d791-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5d791-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d791-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d791-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="5d791-106">Kapatılacak numaralandırmanın tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="5d791-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d791-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5d791-107">Return Value</span></span>  

 <span data-ttu-id="5d791-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d791-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d791-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d791-109">Requirements</span></span>  

 <span data-ttu-id="5d791-110">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="5d791-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d791-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d791-111">See also</span></span>

- [<span data-ttu-id="5d791-112">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d791-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5d791-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d791-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5d791-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="5d791-114">ALink API</span></span>](index.md)
