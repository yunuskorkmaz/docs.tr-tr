---
title: VerifyClientKey işlevi (Yönetilmeyen API Başvurusu)
description: VerifyClientKey işlevi istemci anahtarının doğru güvenliğe sahip olmasını sağlar.
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
ms.openlocfilehash: ebb794240494deb0c831b50e95461ec52017a215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176714"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="f508a-103">VerifyClientKey işlevi</span><span class="sxs-lookup"><span data-stu-id="f508a-103">VerifyClientKey function</span></span>
<span data-ttu-id="f508a-104">İstemci anahtarının doğru güvenliğe sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f508a-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f508a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f508a-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey();
```  

## <a name="return-value"></a><span data-ttu-id="f508a-106">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="f508a-106">Return value</span></span>

<span data-ttu-id="f508a-107">İşlev başarılı olursa, iade `ERROR_SUCCESS` değeri (0) olur.</span><span class="sxs-lookup"><span data-stu-id="f508a-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="f508a-108">İşlev başarısız olursa, iade değeri *WinError.h'de*tanımlanan sıfır olmayan bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="f508a-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="f508a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f508a-109">Requirements</span></span>  
 <span data-ttu-id="f508a-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f508a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f508a-111">**Üstbilgi:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="f508a-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="f508a-112">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f508a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f508a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f508a-113">See also</span></span>

- [<span data-ttu-id="f508a-114">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f508a-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
