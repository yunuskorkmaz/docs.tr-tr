---
title: GetCORRequiredVersion İşlevi
ms.date: 03/30/2017
api_name:
- GetCORRequiredVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetCORRequiredVersion
helpviewer_keywords:
- GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type:
- apiref
ms.openlocfilehash: 9590d19f4e5f5890af53a108492bd1b6d130fb72
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704506"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="7a44e-102">GetCORRequiredVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="7a44e-102">GetCORRequiredVersion Function</span></span>

<span data-ttu-id="7a44e-103">Gerekli ortak dil çalışma zamanı (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="7a44e-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="7a44e-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="7a44e-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a44e-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7a44e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a44e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a44e-106">Parameters</span></span>  

 `pbuffer`  
 <span data-ttu-id="7a44e-107">dışı Sürüm numarasını belirten bir dize içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="7a44e-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7a44e-108">'ndaki Arabelleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="7a44e-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="7a44e-109">dışı Arabellekte döndürülen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7a44e-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a44e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a44e-110">Requirements</span></span>  

 <span data-ttu-id="7a44e-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a44e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a44e-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7a44e-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7a44e-113">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7a44e-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a44e-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a44e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a44e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a44e-115">See also</span></span>

- [<span data-ttu-id="7a44e-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7a44e-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
