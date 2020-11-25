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
ms.openlocfilehash: 26cffe9936f2e01078b6f54e8499b58519f1018e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729427"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="8ab39-103">VerifyClientKey işlevi</span><span class="sxs-lookup"><span data-stu-id="8ab39-103">VerifyClientKey function</span></span>

<span data-ttu-id="8ab39-104">İstemci anahtarının doğru güvenliğe sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ab39-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="8ab39-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8ab39-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey();
```  

## <a name="return-value"></a><span data-ttu-id="8ab39-106">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="8ab39-106">Return value</span></span>

<span data-ttu-id="8ab39-107">İşlev başarılı olursa, dönüş değeri `ERROR_SUCCESS` (0) olur.</span><span class="sxs-lookup"><span data-stu-id="8ab39-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="8ab39-108">İşlev başarısız olursa, dönüş değeri, *Winerror. h* içinde tanımlanan sıfır olmayan bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="8ab39-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="8ab39-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ab39-109">Requirements</span></span>  

 <span data-ttu-id="8ab39-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ab39-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ab39-111">**Üst bilgi:** WMINet_Utils. def</span><span class="sxs-lookup"><span data-stu-id="8ab39-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="8ab39-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8ab39-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ab39-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ab39-113">See also</span></span>

- [<span data-ttu-id="8ab39-114">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8ab39-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
