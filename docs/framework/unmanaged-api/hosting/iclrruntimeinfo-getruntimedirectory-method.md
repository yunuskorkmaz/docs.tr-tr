---
description: ': ICLRRuntimeInfo:: GetRuntimeDirectory yöntemi hakkında daha fazla bilgi edinin'
title: ICLRRuntimeInfo::GetRuntimeDirectory Metodu
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
ms.openlocfilehash: 1e833887568d0a61e9ff9ec358b6979a4bacce41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637098"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="4fb39-103">ICLRRuntimeInfo::GetRuntimeDirectory Metodu</span><span class="sxs-lookup"><span data-stu-id="4fb39-103">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>

<span data-ttu-id="4fb39-104">Bu arabirimle ilişkili ortak dil çalışma zamanının (CLR) yükleme dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="4fb39-104">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="4fb39-105">Bu yöntem 2,0, 3,0 ve 3,5 .NET Framework sürümlerinde sunulan [GetCORSystemDirectory](getcorsystemdirectory-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="4fb39-105">This method supersedes the [GetCORSystemDirectory](getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fb39-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4fb39-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fb39-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4fb39-107">Parameters</span></span>  

 `pwzBuffer`  
 <span data-ttu-id="4fb39-108">dışı CLR yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4fb39-108">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="4fb39-109">Yükleme yolu tam olarak nitelenir; Örneğin, "c:\Windows\Microsoft.NET\Framework\v1.0.3705 \\ ".</span><span class="sxs-lookup"><span data-stu-id="4fb39-109">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="4fb39-110">[in, out] `pwzBuffer` Arabellek taşmalarını önlemek için boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4fb39-110">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="4fb39-111">`pwzBuffer`Null ise, `pchBuffer` gereken boyutunu döndürür `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="4fb39-111">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4fb39-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4fb39-112">Return Value</span></span>  

 <span data-ttu-id="4fb39-113">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="4fb39-113">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4fb39-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4fb39-114">HRESULT</span></span>|<span data-ttu-id="4fb39-115">Description</span><span class="sxs-lookup"><span data-stu-id="4fb39-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4fb39-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="4fb39-116">S_OK</span></span>|<span data-ttu-id="4fb39-117">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="4fb39-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="4fb39-118">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="4fb39-118">E_POINTER</span></span>|<span data-ttu-id="4fb39-119">`pwzBuffer` ya da `pchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="4fb39-119">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fb39-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4fb39-120">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fb39-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4fb39-121">Requirements</span></span>  

 <span data-ttu-id="4fb39-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fb39-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fb39-123">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="4fb39-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4fb39-124">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4fb39-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fb39-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fb39-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fb39-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fb39-126">See also</span></span>

- [<span data-ttu-id="4fb39-127">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4fb39-127">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="4fb39-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="4fb39-128">Hosting</span></span>](index.md)
