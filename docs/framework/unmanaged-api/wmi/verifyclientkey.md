---
title: VerifyClientKey işlevi (yönetilmeyen API Başvurusu)
description: VerifyClientKey işlevi, istemci anahtarının doğru güvenliğe sahip olmasını sağlar.
ms.date: 11/06/2017
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0a0680651eb192e2798ede00048599c5130e63f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107356"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="b92b9-103">VerifyClientKey işlevi</span><span class="sxs-lookup"><span data-stu-id="b92b9-103">VerifyClientKey function</span></span>
<span data-ttu-id="b92b9-104">İstemci anahtarının doğru güvenliğe sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b92b9-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b92b9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b92b9-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="b92b9-106">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b92b9-106">Return value</span></span>

<span data-ttu-id="b92b9-107">İşlev başarılı olursa, dönüş değeri `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="b92b9-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="b92b9-108">İşlev başarısız olursa, dönüş değeri, *Winerror. h*içinde tanımlanan sıfır olmayan bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="b92b9-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="b92b9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b92b9-109">Requirements</span></span>  
 <span data-ttu-id="b92b9-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b92b9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b92b9-111">**Üst bilgi:** WMINet_Utils. def</span><span class="sxs-lookup"><span data-stu-id="b92b9-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="b92b9-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b92b9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b92b9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b92b9-113">See also</span></span>

- [<span data-ttu-id="b92b9-114">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b92b9-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
