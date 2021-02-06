---
description: ': ICLRRuntimeInfo:: GetProcAddress yöntemi hakkında daha fazla bilgi edinin'
title: ICLRRuntimeInfo::GetProcAddress Metodu
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
ms.openlocfilehash: 1e5d08ed118930418106b28541b4081d6acad927
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637150"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="3f4bd-103">ICLRRuntimeInfo::GetProcAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="3f4bd-103">ICLRRuntimeInfo::GetProcAddress Method</span></span>

<span data-ttu-id="3f4bd-104">Bu arabirimle ilişkili ortak dil çalışma zamanından (CLR) aktarılmış olan belirli bir işlevin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="3f4bd-104">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="3f4bd-105">Bu yöntem [GetRealProcAddress](getrealprocaddress-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="3f4bd-105">This method supersedes the [GetRealProcAddress](getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f4bd-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f4bd-106">Syntax</span></span>  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f4bd-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f4bd-107">Parameters</span></span>  

 `pszProcName`  
 <span data-ttu-id="3f4bd-108">'ndaki İçe aktarılmış işlevin adı.</span><span class="sxs-lookup"><span data-stu-id="3f4bd-108">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="3f4bd-109">dışı İçe aktarılmış işlevin adresi.</span><span class="sxs-lookup"><span data-stu-id="3f4bd-109">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f4bd-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3f4bd-110">Return Value</span></span>  

 <span data-ttu-id="3f4bd-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="3f4bd-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3f4bd-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3f4bd-112">HRESULT</span></span>|<span data-ttu-id="3f4bd-113">Description</span><span class="sxs-lookup"><span data-stu-id="3f4bd-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f4bd-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="3f4bd-114">S_OK</span></span>|<span data-ttu-id="3f4bd-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="3f4bd-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="3f4bd-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3f4bd-116">E_POINTER</span></span>|<span data-ttu-id="3f4bd-117">`pszProcName` ya da `ppProc` null.</span><span class="sxs-lookup"><span data-stu-id="3f4bd-117">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="3f4bd-118">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="3f4bd-118">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="3f4bd-119">Belirtilen işlev, dışarıya aktarılmış bir işlev değil.</span><span class="sxs-lookup"><span data-stu-id="3f4bd-119">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f4bd-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f4bd-120">Remarks</span></span>  

 <span data-ttu-id="3f4bd-121">Bu yöntem CLR 'nin yüklenmesine, ancak başlatılmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f4bd-121">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f4bd-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f4bd-122">Requirements</span></span>  

 <span data-ttu-id="3f4bd-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f4bd-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f4bd-124">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="3f4bd-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3f4bd-125">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3f4bd-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f4bd-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f4bd-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f4bd-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f4bd-127">See also</span></span>

- [<span data-ttu-id="3f4bd-128">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f4bd-128">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="3f4bd-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3f4bd-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="3f4bd-130">Hosting</span><span class="sxs-lookup"><span data-stu-id="3f4bd-130">Hosting</span></span>](index.md)
