---
description: 'Daha fazla bilgi edinin: CloseEnum Yöntemi'
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
ms.openlocfilehash: 700c54de5af2e5c0be6940d4045019092655d46f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638385"
---
# <a name="closeenum-method"></a><span data-ttu-id="215fa-103">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="215fa-103">CloseEnum Method</span></span>

<span data-ttu-id="215fa-104">Belirtilen numaralandırmayı kapatır ve ilişkili kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="215fa-104">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="215fa-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="215fa-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="215fa-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="215fa-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="215fa-107">Kapatılacak numaralandırmanın tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="215fa-107">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="215fa-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="215fa-108">Return Value</span></span>  

 <span data-ttu-id="215fa-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="215fa-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="215fa-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="215fa-110">Requirements</span></span>  

 <span data-ttu-id="215fa-111">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="215fa-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215fa-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="215fa-112">See also</span></span>

- [<span data-ttu-id="215fa-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="215fa-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="215fa-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="215fa-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="215fa-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="215fa-115">ALink API</span></span>](index.md)
