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
ms.openlocfilehash: 6b9fd62102056a8d5f859ac913f4786f04c1df7e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617249"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="2e8f9-102">GetCORRequiredVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="2e8f9-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="2e8f9-103">Gerekli ortak dil çalışma zamanı (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="2e8f9-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="2e8f9-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="2e8f9-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e8f9-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2e8f9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e8f9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e8f9-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="2e8f9-107">dışı Sürüm numarasını belirten bir dize içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="2e8f9-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2e8f9-108">'ndaki Arabelleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="2e8f9-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2e8f9-109">dışı Arabellekte döndürülen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="2e8f9-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e8f9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e8f9-110">Requirements</span></span>  
 <span data-ttu-id="2e8f9-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e8f9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e8f9-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2e8f9-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e8f9-113">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2e8f9-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e8f9-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e8f9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e8f9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e8f9-115">See also</span></span>

- [<span data-ttu-id="2e8f9-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2e8f9-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
