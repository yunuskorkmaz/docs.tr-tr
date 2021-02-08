---
description: 'Daha fazla bilgi edinin: GetCORSystemDirectory Işlevi'
title: GetCORSystemDirectory İşlevi
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: 267736c2f8cdea03fbd9f77108a3d88193830ab4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785347"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="0f8e9-103">GetCORSystemDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="0f8e9-103">GetCORSystemDirectory Function</span></span>

<span data-ttu-id="0f8e9-104">İşleme yüklenen ortak dil çalışma zamanının (CLR) yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f8e9-104">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="0f8e9-105">Yükleme dizini tam olarak nitelenir, örneğin "c:\Windows\Microsoft.NET\Framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="0f8e9-105">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="0f8e9-106">Bu işlev kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="0f8e9-106">This function is deprecated.</span></span> <span data-ttu-id="0f8e9-107">.NET Framework 4 ' te belirtilen [ICLRRuntimeInfo:: GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) yöntemi ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0f8e9-107">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f8e9-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f8e9-108">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="0f8e9-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f8e9-109">Parameters</span></span>  

 `pbuffer`  
 <span data-ttu-id="0f8e9-110">dışı Çalışma zamanının, işleme yüklenmiş çalışma zamanı için yükleme dizininin tam adını içeren bir dize döndürdüğü bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="0f8e9-110">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="0f8e9-111">Çalışma zamanı işleme henüz yüklenmemişse, işlev, bilgisayarda yüklü olan çalışma zamanının en son sürümü için uygun dizin bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f8e9-111">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="0f8e9-112">'ndaki Bayt cinsinden boyutu `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="0f8e9-112">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="0f8e9-113">dışı İçinde döndürülen karakterlerin sayısı `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="0f8e9-113">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f8e9-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f8e9-114">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="0f8e9-115">Bu işlevi CLR sürüm 4 ' ü çalıştıran işlemlerde kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="0f8e9-115">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="0f8e9-116">Bilgisayarda CLR 'nin önceki bir sürümü yüklüyse, bu işlev söz konusu sürümün yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f8e9-116">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f8e9-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f8e9-117">Requirements</span></span>  

 <span data-ttu-id="0f8e9-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f8e9-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f8e9-119">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0f8e9-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f8e9-120">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0f8e9-120">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f8e9-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f8e9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f8e9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f8e9-122">See also</span></span>

- [<span data-ttu-id="0f8e9-123">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0f8e9-123">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
