---
title: VerifyClientKey işlevi (yönetilmeyen API Başvurusu)
description: Doğru güvenlik istemci anahtara sahip VerifyClientKey işlevi sağlar.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea8a74633d3e950f6cf7ba87c00a9efa45206545
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459570"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="a3ee8-103">VerifyClientKey işlevi</span><span class="sxs-lookup"><span data-stu-id="a3ee8-103">VerifyClientKey function</span></span>
<span data-ttu-id="a3ee8-104">İstemci anahtar doğru güvenlik sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3ee8-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a3ee8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3ee8-105">Syntax</span></span>  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="a3ee8-106">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="a3ee8-106">Return value</span></span>

<span data-ttu-id="a3ee8-107">İşlev başarılı olursa, dönüş değeri olan `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="a3ee8-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="a3ee8-108">İşlev başarısız olursa, dönüş değeri tanımlanan bir sıfır olmayan bir hata kodu *Winerror.h'de*.</span><span class="sxs-lookup"><span data-stu-id="a3ee8-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="a3ee8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3ee8-109">Requirements</span></span>  
 <span data-ttu-id="a3ee8-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3ee8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3ee8-111">**Başlık:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="a3ee8-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="a3ee8-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a3ee8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ee8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3ee8-113">See also</span></span>  
[<span data-ttu-id="a3ee8-114">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a3ee8-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
