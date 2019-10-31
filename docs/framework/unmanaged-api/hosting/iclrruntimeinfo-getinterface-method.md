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
ms.openlocfilehash: 295deeec2e8eb42ccaa4d0cfb8b08b32438d047c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120246"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="00d13-102">ICLRRuntimeInfo::GetInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="00d13-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="00d13-103">CLR 'yi geçerli işleme yükler ve [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)ve [ımetadatadağıtıserex](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)gibi çalışma zamanı arabirimi işaretçilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="00d13-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="00d13-104">Bu yöntem, [kullanımdan KALDıRıLAN clr barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) bölümündeki tüm `CorBindTo`\* işlevlerinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="00d13-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00d13-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00d13-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00d13-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="00d13-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="00d13-107">'ndaki Coclass için CLSID arabirimi.</span><span class="sxs-lookup"><span data-stu-id="00d13-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="00d13-108">'ndaki İstenen `rclsid` arabiriminin IID 'si.</span><span class="sxs-lookup"><span data-stu-id="00d13-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="00d13-109">dışı Sorgulanan arabirime yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="00d13-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00d13-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="00d13-110">Return Value</span></span>  
 <span data-ttu-id="00d13-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="00d13-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="00d13-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="00d13-112">HRESULT</span></span>|<span data-ttu-id="00d13-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00d13-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00d13-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="00d13-114">S_OK</span></span>|<span data-ttu-id="00d13-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="00d13-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="00d13-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="00d13-116">E_POINTER</span></span>|<span data-ttu-id="00d13-117">`ppUnk` null.</span><span class="sxs-lookup"><span data-stu-id="00d13-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="00d13-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="00d13-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="00d13-119">İsteği işlemek için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="00d13-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="00d13-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="00d13-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="00d13-121">Farklı bir çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesine zaten bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="00d13-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00d13-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00d13-122">Remarks</span></span>  
 <span data-ttu-id="00d13-123">Bu yöntem CLR 'nin yüklenmesine, ancak başlatılmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="00d13-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="00d13-124">Aşağıdaki tabloda `rclsid` ve `riid`için desteklenen birleşimler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="00d13-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="00d13-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="00d13-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="00d13-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="00d13-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="00d13-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="00d13-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="00d13-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="00d13-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="00d13-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="00d13-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="00d13-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="00d13-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="00d13-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="00d13-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="00d13-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="00d13-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="00d13-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="00d13-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="00d13-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="00d13-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="00d13-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="00d13-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="00d13-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="00d13-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="00d13-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="00d13-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="00d13-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="00d13-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00d13-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00d13-139">Requirements</span></span>  
 <span data-ttu-id="00d13-140">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00d13-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00d13-141">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="00d13-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="00d13-142">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="00d13-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00d13-143">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00d13-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d13-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00d13-144">See also</span></span>

- [<span data-ttu-id="00d13-145">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00d13-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="00d13-146">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="00d13-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="00d13-147">Barındırma</span><span class="sxs-lookup"><span data-stu-id="00d13-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
