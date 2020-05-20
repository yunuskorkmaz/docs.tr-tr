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
ms.openlocfilehash: c8ac959c192814562488ab916c8462b0baa0d8e6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703654"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="fa1d2-102">ICLRRuntimeInfo::GetInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="fa1d2-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="fa1d2-103">CLR 'yi geçerli işleme yükler ve [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)ve [ımetadatadağıtıserex](../metadata/imetadatadispenser-interface.md)gibi çalışma zamanı arabirimi işaretçilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa1d2-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="fa1d2-104">Bu yöntem, `CorBindTo` [KULLANıMDAN kaldırılan clr barındırma işlevleri](deprecated-clr-hosting-functions.md) bölümündeki tüm \* işlevlerinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="fa1d2-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa1d2-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fa1d2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa1d2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa1d2-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="fa1d2-107">'ndaki Coclass için CLSID arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fa1d2-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="fa1d2-108">'ndaki İstenen arabirimin IID 'si `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="fa1d2-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="fa1d2-109">dışı Sorgulanan arabirime yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fa1d2-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa1d2-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fa1d2-110">Return Value</span></span>  
 <span data-ttu-id="fa1d2-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa1d2-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fa1d2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa1d2-112">HRESULT</span></span>|<span data-ttu-id="fa1d2-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa1d2-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa1d2-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa1d2-114">S_OK</span></span>|<span data-ttu-id="fa1d2-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="fa1d2-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="fa1d2-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="fa1d2-116">E_POINTER</span></span>|<span data-ttu-id="fa1d2-117">`ppUnk`null.</span><span class="sxs-lookup"><span data-stu-id="fa1d2-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="fa1d2-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="fa1d2-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="fa1d2-119">İsteği işlemek için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="fa1d2-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="fa1d2-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="fa1d2-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="fa1d2-121">Farklı bir çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesine zaten bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="fa1d2-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa1d2-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa1d2-122">Remarks</span></span>  
 <span data-ttu-id="fa1d2-123">Bu yöntem CLR 'nin yüklenmesine, ancak başlatılmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa1d2-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="fa1d2-124">Aşağıdaki tabloda ve için desteklenen birleşimler gösterilmektedir `rclsid` `riid` .</span><span class="sxs-lookup"><span data-stu-id="fa1d2-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="fa1d2-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="fa1d2-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="fa1d2-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="fa1d2-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="fa1d2-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="fa1d2-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="fa1d2-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="fa1d2-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="fa1d2-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="fa1d2-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="fa1d2-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="fa1d2-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="fa1d2-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="fa1d2-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="fa1d2-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="fa1d2-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="fa1d2-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="fa1d2-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="fa1d2-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="fa1d2-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="fa1d2-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="fa1d2-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="fa1d2-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="fa1d2-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="fa1d2-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="fa1d2-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="fa1d2-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="fa1d2-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fa1d2-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa1d2-139">Requirements</span></span>  
 <span data-ttu-id="fa1d2-140">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa1d2-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa1d2-141">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="fa1d2-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fa1d2-142">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="fa1d2-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa1d2-143">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa1d2-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa1d2-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa1d2-144">See also</span></span>

- [<span data-ttu-id="fa1d2-145">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa1d2-145">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="fa1d2-146">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fa1d2-146">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="fa1d2-147">Barındırma</span><span class="sxs-lookup"><span data-stu-id="fa1d2-147">Hosting</span></span>](index.md)
