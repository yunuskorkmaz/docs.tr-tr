---
title: ICLRRuntimeInfo::GetInterface Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3c5150a10a813da85fc035c7bfa43a7647fac308
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="541c0-102">ICLRRuntimeInfo::GetInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="541c0-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="541c0-103">CLR geçerli sürecine yükler ve çalışma zamanı arabirim işaretçileri gibi döndürür [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), ve [Imetadatadispenserex](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="541c0-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="541c0-104">Bu yöntem tüm yerini `CorBindTo`\* işlevlerini [kullanım dışı CLR barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) bölümü.</span><span class="sxs-lookup"><span data-stu-id="541c0-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="541c0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="541c0-105">Syntax</span></span>  
  
```  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="541c0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="541c0-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="541c0-107">[in] Coclass'ı CLSID arabirimi.</span><span class="sxs-lookup"><span data-stu-id="541c0-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="541c0-108">[in] İstenen IID `rclsid` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="541c0-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="541c0-109">[out] Sorgulanan arabirimi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="541c0-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="541c0-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="541c0-110">Return Value</span></span>  
 <span data-ttu-id="541c0-111">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="541c0-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="541c0-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="541c0-112">HRESULT</span></span>|<span data-ttu-id="541c0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="541c0-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="541c0-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="541c0-114">S_OK</span></span>|<span data-ttu-id="541c0-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="541c0-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="541c0-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="541c0-116">E_POINTER</span></span>|<span data-ttu-id="541c0-117">`ppUnk`null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="541c0-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="541c0-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="541c0-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="541c0-119">İsteği işlemek yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="541c0-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="541c0-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="541c0-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="541c0-121">Farklı bir çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesi zaten bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="541c0-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="541c0-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="541c0-122">Remarks</span></span>  
 <span data-ttu-id="541c0-123">Bu yöntem yüklendi ancak başlatılmadı CLR neden olur.</span><span class="sxs-lookup"><span data-stu-id="541c0-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="541c0-124">Aşağıdaki tablo için desteklenen birleşimlerin gösterir `rclsid` ve `riid`.</span><span class="sxs-lookup"><span data-stu-id="541c0-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="541c0-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="541c0-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="541c0-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="541c0-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="541c0-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="541c0-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="541c0-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="541c0-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="541c0-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="541c0-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="541c0-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="541c0-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="541c0-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="541c0-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="541c0-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="541c0-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="541c0-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="541c0-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="541c0-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="541c0-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="541c0-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="541c0-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="541c0-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="541c0-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="541c0-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="541c0-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="541c0-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="541c0-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="541c0-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="541c0-139">Requirements</span></span>  
 <span data-ttu-id="541c0-140">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="541c0-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="541c0-141">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="541c0-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="541c0-142">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="541c0-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="541c0-143">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="541c0-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="541c0-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="541c0-144">See Also</span></span>  
 [<span data-ttu-id="541c0-145">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="541c0-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="541c0-146">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="541c0-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="541c0-147">Barındırma</span><span class="sxs-lookup"><span data-stu-id="541c0-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
