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
ms.openlocfilehash: 9cf9d48bf50ffc1fc56270c13215acfef6d9c3af
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504062"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="a5b36-102">ICLRRuntimeInfo::GetInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="a5b36-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="a5b36-103">CLR 'yi geçerli işleme yükler ve [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md)ve [ımetadatadağıtıserex](../metadata/imetadatadispenser-interface.md)gibi çalışma zamanı arabirimi işaretçilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a5b36-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md), and [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="a5b36-104">Bu yöntem, `CorBindTo` [KULLANıMDAN kaldırılan clr barındırma işlevleri](deprecated-clr-hosting-functions.md) bölümündeki tüm \* işlevlerinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="a5b36-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5b36-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a5b36-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5b36-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5b36-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="a5b36-107">'ndaki Coclass için CLSID arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a5b36-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="a5b36-108">'ndaki İstenen arabirimin IID 'si `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="a5b36-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="a5b36-109">dışı Sorgulanan arabirime yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a5b36-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5b36-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a5b36-110">Return Value</span></span>  
 <span data-ttu-id="a5b36-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="a5b36-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a5b36-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5b36-112">HRESULT</span></span>|<span data-ttu-id="a5b36-113">Description</span><span class="sxs-lookup"><span data-stu-id="a5b36-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5b36-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5b36-114">S_OK</span></span>|<span data-ttu-id="a5b36-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="a5b36-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="a5b36-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="a5b36-116">E_POINTER</span></span>|<span data-ttu-id="a5b36-117">`ppUnk`null.</span><span class="sxs-lookup"><span data-stu-id="a5b36-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="a5b36-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a5b36-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a5b36-119">İsteği işlemek için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="a5b36-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="a5b36-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="a5b36-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="a5b36-121">Farklı bir çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesine zaten bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="a5b36-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5b36-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5b36-122">Remarks</span></span>  
 <span data-ttu-id="a5b36-123">Bu yöntem CLR 'nin yüklenmesine, ancak başlatılmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a5b36-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="a5b36-124">Aşağıdaki tabloda ve için desteklenen birleşimler gösterilmektedir `rclsid` `riid` .</span><span class="sxs-lookup"><span data-stu-id="a5b36-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="a5b36-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="a5b36-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="a5b36-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="a5b36-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="a5b36-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="a5b36-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="a5b36-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="a5b36-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="a5b36-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="a5b36-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="a5b36-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="a5b36-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="a5b36-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="a5b36-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="a5b36-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="a5b36-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="a5b36-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="a5b36-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="a5b36-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="a5b36-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="a5b36-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="a5b36-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="a5b36-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="a5b36-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="a5b36-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="a5b36-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="a5b36-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="a5b36-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5b36-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5b36-139">Requirements</span></span>  
 <span data-ttu-id="a5b36-140">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5b36-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5b36-141">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="a5b36-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a5b36-142">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a5b36-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5b36-143">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5b36-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b36-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5b36-144">See also</span></span>

- [<span data-ttu-id="a5b36-145">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5b36-145">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="a5b36-146">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a5b36-146">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="a5b36-147">Hosting</span><span class="sxs-lookup"><span data-stu-id="a5b36-147">Hosting</span></span>](index.md)
