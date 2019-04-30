---
title: ICLRRuntimeInfo::GetInterface Metodu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f229e421cc69f2ff45110233c4c6c36d7a1fc4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771767"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="aed0d-102">ICLRRuntimeInfo::GetInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="aed0d-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="aed0d-103">Geçerli işleme CLR yükler ve çalışma zamanı arabirim işaretçileri gibi döndürür [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), ve [Imetadatadispenserex](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="aed0d-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="aed0d-104">Bu yöntem tüm yerini `CorBindTo`\* içindeki işlevler [kullanım dışı CLR barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) bölümü.</span><span class="sxs-lookup"><span data-stu-id="aed0d-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aed0d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aed0d-105">Syntax</span></span>  
  
```  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aed0d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aed0d-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="aed0d-107">[in] Coclass'ı CLSID arabirimi.</span><span class="sxs-lookup"><span data-stu-id="aed0d-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="aed0d-108">[in] İstenen Laboratuvardaki `rclsid` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="aed0d-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="aed0d-109">[out] Sorgulanan arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="aed0d-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aed0d-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aed0d-110">Return Value</span></span>  
 <span data-ttu-id="aed0d-111">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="aed0d-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="aed0d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aed0d-112">HRESULT</span></span>|<span data-ttu-id="aed0d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aed0d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aed0d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="aed0d-114">S_OK</span></span>|<span data-ttu-id="aed0d-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="aed0d-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="aed0d-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="aed0d-116">E_POINTER</span></span>|<span data-ttu-id="aed0d-117">`ppUnk` NULL olur.</span><span class="sxs-lookup"><span data-stu-id="aed0d-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="aed0d-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="aed0d-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="aed0d-119">İsteği işlemek yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="aed0d-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="aed0d-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="aed0d-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="aed0d-121">Farklı bir çalışma zamanı, eski CLR sürüm 2 etkinleştirme ilkesi zaten bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="aed0d-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aed0d-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aed0d-122">Remarks</span></span>  
 <span data-ttu-id="aed0d-123">Bu yöntem CLR'nin yüklendi ancak başlatılmadı neden olur.</span><span class="sxs-lookup"><span data-stu-id="aed0d-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="aed0d-124">Aşağıdaki tablo için desteklenen kombinasyonlar gösterir `rclsid` ve `riid`.</span><span class="sxs-lookup"><span data-stu-id="aed0d-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="aed0d-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="aed0d-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="aed0d-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="aed0d-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="aed0d-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="aed0d-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="aed0d-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="aed0d-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="aed0d-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="aed0d-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="aed0d-130">: Iıd_ıcorruntimehost</span><span class="sxs-lookup"><span data-stu-id="aed0d-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="aed0d-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="aed0d-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="aed0d-132">Iıd_ıclrruntimehost</span><span class="sxs-lookup"><span data-stu-id="aed0d-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="aed0d-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="aed0d-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="aed0d-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="aed0d-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="aed0d-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="aed0d-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="aed0d-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="aed0d-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="aed0d-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="aed0d-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="aed0d-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="aed0d-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aed0d-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aed0d-139">Requirements</span></span>  
 <span data-ttu-id="aed0d-140">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aed0d-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aed0d-141">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="aed0d-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="aed0d-142">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="aed0d-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aed0d-143">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aed0d-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aed0d-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aed0d-144">See also</span></span>

- [<span data-ttu-id="aed0d-145">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aed0d-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="aed0d-146">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aed0d-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="aed0d-147">Barındırma</span><span class="sxs-lookup"><span data-stu-id="aed0d-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
