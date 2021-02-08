---
description: ': GetRequestedRuntimeVersion Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 836cc4b875ddc427c6779950f5b68d2df8b6ef75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785282"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="fbc50-103">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="fbc50-103">GetRequestedRuntimeVersion Function</span></span>

<span data-ttu-id="fbc50-104">Belirtilen uygulama tarafından istenen ortak dil çalışma zamanının (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="fbc50-104">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="fbc50-105">Bu sürüm yüklü değilse, istenen sürümden önce yüklenen en son sürümü alır.</span><span class="sxs-lookup"><span data-stu-id="fbc50-105">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="fbc50-106">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="fbc50-106">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbc50-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fbc50-107">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbc50-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fbc50-108">Parameters</span></span>  

 `pExe`  
 <span data-ttu-id="fbc50-109">'ndaki Uygulamanın adı.</span><span class="sxs-lookup"><span data-stu-id="fbc50-109">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="fbc50-110">dışı Başarılı bir şekilde tamamlandıktan sonra sürüm numarası dizesini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="fbc50-110">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="fbc50-111">'ndaki Sürüm arabelleğinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="fbc50-111">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="fbc50-112">dışı Sürüm numarası dizesinin uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fbc50-112">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbc50-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fbc50-113">Return Value</span></span>  

 <span data-ttu-id="fbc50-114">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="fbc50-114">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="fbc50-115">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="fbc50-115">Return code</span></span>|<span data-ttu-id="fbc50-116">Description</span><span class="sxs-lookup"><span data-stu-id="fbc50-116">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="fbc50-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="fbc50-117">S_OK</span></span>|<span data-ttu-id="fbc50-118">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="fbc50-118">The method completed successfully.</span></span>|  
|<span data-ttu-id="fbc50-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="fbc50-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="fbc50-120">Sürüm arabelleği, sürüm dizesini depolamak için yeterince büyük değil.</span><span class="sxs-lookup"><span data-stu-id="fbc50-120">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="fbc50-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="fbc50-121">E_POINTER</span></span>|<span data-ttu-id="fbc50-122">`pdwLength` null.</span><span class="sxs-lookup"><span data-stu-id="fbc50-122">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fbc50-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fbc50-123">Requirements</span></span>  

 <span data-ttu-id="fbc50-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbc50-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbc50-125">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fbc50-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fbc50-126">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fbc50-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbc50-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbc50-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc50-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbc50-128">See also</span></span>

- [<span data-ttu-id="fbc50-129">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="fbc50-129">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="fbc50-130">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="fbc50-130">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="fbc50-131">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fbc50-131">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
