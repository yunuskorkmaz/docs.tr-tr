---
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
ms.openlocfilehash: 028cfd51a713d8598598566a5b1edcf3fc70ecfc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732066"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="3c843-102">ICLRRuntimeInfo::GetProcAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="3c843-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>

<span data-ttu-id="3c843-103">Bu arabirimle ilişkili ortak dil çalışma zamanından (CLR) aktarılmış olan belirli bir işlevin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="3c843-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="3c843-104">Bu yöntem [GetRealProcAddress](getrealprocaddress-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="3c843-104">This method supersedes the [GetRealProcAddress](getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c843-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3c843-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c843-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c843-106">Parameters</span></span>  

 `pszProcName`  
 <span data-ttu-id="3c843-107">'ndaki İçe aktarılmış işlevin adı.</span><span class="sxs-lookup"><span data-stu-id="3c843-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="3c843-108">dışı İçe aktarılmış işlevin adresi.</span><span class="sxs-lookup"><span data-stu-id="3c843-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c843-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3c843-109">Return Value</span></span>  

 <span data-ttu-id="3c843-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="3c843-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3c843-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3c843-111">HRESULT</span></span>|<span data-ttu-id="3c843-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c843-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3c843-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="3c843-113">S_OK</span></span>|<span data-ttu-id="3c843-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="3c843-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="3c843-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3c843-115">E_POINTER</span></span>|<span data-ttu-id="3c843-116">`pszProcName` ya da `ppProc` null.</span><span class="sxs-lookup"><span data-stu-id="3c843-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="3c843-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="3c843-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="3c843-118">Belirtilen işlev, dışarıya aktarılmış bir işlev değil.</span><span class="sxs-lookup"><span data-stu-id="3c843-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c843-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c843-119">Remarks</span></span>  

 <span data-ttu-id="3c843-120">Bu yöntem CLR 'nin yüklenmesine, ancak başlatılmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c843-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c843-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c843-121">Requirements</span></span>  

 <span data-ttu-id="3c843-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c843-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c843-123">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="3c843-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3c843-124">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3c843-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c843-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c843-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c843-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c843-126">See also</span></span>

- [<span data-ttu-id="3c843-127">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c843-127">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="3c843-128">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3c843-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="3c843-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="3c843-129">Hosting</span></span>](index.md)
