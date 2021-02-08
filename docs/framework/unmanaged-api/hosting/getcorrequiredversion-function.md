---
description: 'Daha fazla bilgi edinin: GetCORRequiredVersion Işlevi'
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
ms.openlocfilehash: ea1b928054e3ec6080b00e2a41228035f50c0f84
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785360"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="a7b43-103">GetCORRequiredVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="a7b43-103">GetCORRequiredVersion Function</span></span>

<span data-ttu-id="a7b43-104">Gerekli ortak dil çalışma zamanı (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="a7b43-104">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="a7b43-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="a7b43-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7b43-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7b43-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7b43-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7b43-107">Parameters</span></span>  

 `pbuffer`  
 <span data-ttu-id="a7b43-108">dışı Sürüm numarasını belirten bir dize içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="a7b43-108">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="a7b43-109">'ndaki Arabelleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="a7b43-109">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="a7b43-110">dışı Arabellekte döndürülen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="a7b43-110">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7b43-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7b43-111">Requirements</span></span>  

 <span data-ttu-id="a7b43-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7b43-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7b43-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a7b43-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7b43-114">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7b43-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7b43-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7b43-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b43-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7b43-116">See also</span></span>

- [<span data-ttu-id="a7b43-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a7b43-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
