---
description: 'Daha fazla bilgi edinin: GetFileVersion Işlevi'
title: GetFileVersion İşlevi
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
ms.openlocfilehash: 7de19484f2f8123d61eb94e6a5ae09f56a3b5541
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785308"
---
# <a name="getfileversion-function"></a><span data-ttu-id="d6ab1-103">GetFileVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="d6ab1-103">GetFileVersion Function</span></span>

<span data-ttu-id="d6ab1-104">Belirtilen arabelleği kullanarak belirtilen dosyanın ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="d6ab1-104">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="d6ab1-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="d6ab1-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ab1-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6ab1-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6ab1-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6ab1-107">Parameters</span></span>  

 `szFilename`  
 <span data-ttu-id="d6ab1-108">'ndaki İnceedilecek dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="d6ab1-108">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="d6ab1-109">[in, out] Döndürülen sürüm bilgileri için ayrılan arabellek.</span><span class="sxs-lookup"><span data-stu-id="d6ab1-109">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="d6ab1-110">'ndaki Öğesinin geniş karakterdeki boyutu `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="d6ab1-110">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="d6ab1-111">dışı Döndürülen bayt cinsinden boyutu `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="d6ab1-111">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6ab1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6ab1-112">Requirements</span></span>  

 <span data-ttu-id="d6ab1-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6ab1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6ab1-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d6ab1-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6ab1-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6ab1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ab1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6ab1-116">See also</span></span>

- [<span data-ttu-id="d6ab1-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d6ab1-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
