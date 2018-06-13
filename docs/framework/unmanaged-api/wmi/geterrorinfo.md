---
title: Geterrorınfo işlevi (yönetilmeyen API Başvurusu)
description: Geterrorınfo işlevi önceki işlev çağrısında hata bilgilerini alır.
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef52a4e503597e08eae407571f02bf63adafc4e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455966"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="83f16-103">Geterrorınfo işlevi</span><span class="sxs-lookup"><span data-stu-id="83f16-103">GetErrorInfo function</span></span>
<span data-ttu-id="83f16-104">Önceki işlev çağrısında hata bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="83f16-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="83f16-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83f16-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="83f16-106">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="83f16-106">Return value</span></span>

<span data-ttu-id="83f16-107">Bir işaretçi bir [IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx) işlev çağrısı başarılı olursa, nesne veya `null` başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="83f16-107">An pointer to an [IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="83f16-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83f16-108">Remarks</span></span>

<span data-ttu-id="83f16-109">Bu işlev çağrısı sarmalar [IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="83f16-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="83f16-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83f16-110">Requirements</span></span>  
 <span data-ttu-id="83f16-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83f16-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83f16-112">**Başlık:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="83f16-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="83f16-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="83f16-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f16-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83f16-114">See also</span></span>  
[<span data-ttu-id="83f16-115">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="83f16-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
