---
title: GetRequestedRuntimeVersion İşlevi
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
ms.openlocfilehash: 6be0bc5d08f612dcb8ed7d256711e0c4367b9274
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178132"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="ae6dc-102">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="ae6dc-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="ae6dc-103">Belirtilen uygulama tarafından istenen ortak dil çalışma zamanının (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="ae6dc-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="ae6dc-104">Bu sürüm yüklenmezse, istenen sürümden önce yüklenen en son sürümü alır.</span><span class="sxs-lookup"><span data-stu-id="ae6dc-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="ae6dc-105">Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ae6dc-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae6dc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae6dc-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae6dc-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae6dc-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="ae6dc-108">[içinde] Uygulamanın adı.</span><span class="sxs-lookup"><span data-stu-id="ae6dc-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="ae6dc-109">[çıkış] Başarılı bir şekilde tamamlandıktan sonra sürüm numarası dizesini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="ae6dc-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="ae6dc-110">[içinde] Sürüm arabelleği uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="ae6dc-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="ae6dc-111">[çıkış] Sürüm numarası dizesinin uzunluğuna işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ae6dc-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae6dc-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ae6dc-112">Return Value</span></span>  
 <span data-ttu-id="ae6dc-113">Bu yöntem, aşağıdaki değerlere ek olarak WinError.h'de tanımlandığı şekilde standart Bileşen Nesne Modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="ae6dc-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="ae6dc-114">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="ae6dc-114">Return code</span></span>|<span data-ttu-id="ae6dc-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae6dc-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ae6dc-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae6dc-116">S_OK</span></span>|<span data-ttu-id="ae6dc-117">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="ae6dc-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="ae6dc-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ae6dc-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ae6dc-119">Sürüm arabelleği sürüm dizesini depolamak için yeterince büyük değildir.</span><span class="sxs-lookup"><span data-stu-id="ae6dc-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="ae6dc-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ae6dc-120">E_POINTER</span></span>|<span data-ttu-id="ae6dc-121">`pdwLength`hükümsüzdür.</span><span class="sxs-lookup"><span data-stu-id="ae6dc-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae6dc-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae6dc-122">Requirements</span></span>  
 <span data-ttu-id="ae6dc-123">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae6dc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae6dc-124">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ae6dc-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae6dc-125">**Kütüphane:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ae6dc-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae6dc-126">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae6dc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae6dc-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae6dc-127">See also</span></span>

- [<span data-ttu-id="ae6dc-128">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="ae6dc-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="ae6dc-129">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="ae6dc-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="ae6dc-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ae6dc-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
