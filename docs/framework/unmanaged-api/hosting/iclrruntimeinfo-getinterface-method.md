---
description: ': ICLRRuntimeInfo:: GetInterface yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5a5c55823ff9954735a712423d8aaab1256c947d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637137"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="14a08-103">ICLRRuntimeInfo::GetInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="14a08-103">ICLRRuntimeInfo::GetInterface Method</span></span>

<span data-ttu-id="14a08-104">CLR 'yi geçerli işleme yükler ve [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md)ve [ımetadatadağıtıserex](../metadata/imetadatadispenser-interface.md)gibi çalışma zamanı arabirimi işaretçilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="14a08-104">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md), and [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="14a08-105">Bu yöntem, `CorBindTo` [KULLANıMDAN kaldırılan clr barındırma işlevleri](deprecated-clr-hosting-functions.md) bölümündeki tüm \* işlevlerinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="14a08-105">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14a08-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14a08-106">Syntax</span></span>  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14a08-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14a08-107">Parameters</span></span>  

 `rclsid`  
 <span data-ttu-id="14a08-108">'ndaki Coclass için CLSID arabirimi.</span><span class="sxs-lookup"><span data-stu-id="14a08-108">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="14a08-109">'ndaki İstenen arabirimin IID 'si `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="14a08-109">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="14a08-110">dışı Sorgulanan arabirime yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="14a08-110">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14a08-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="14a08-111">Return Value</span></span>  

 <span data-ttu-id="14a08-112">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="14a08-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="14a08-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="14a08-113">HRESULT</span></span>|<span data-ttu-id="14a08-114">Description</span><span class="sxs-lookup"><span data-stu-id="14a08-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14a08-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="14a08-115">S_OK</span></span>|<span data-ttu-id="14a08-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="14a08-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="14a08-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="14a08-117">E_POINTER</span></span>|<span data-ttu-id="14a08-118">`ppUnk` null.</span><span class="sxs-lookup"><span data-stu-id="14a08-118">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="14a08-119">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="14a08-119">E_OUTOFMEMORY</span></span>|<span data-ttu-id="14a08-120">İsteği işlemek için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="14a08-120">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="14a08-121">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="14a08-121">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="14a08-122">Farklı bir çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesine zaten bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="14a08-122">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14a08-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14a08-123">Remarks</span></span>  

 <span data-ttu-id="14a08-124">Bu yöntem CLR 'nin yüklenmesine, ancak başlatılmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="14a08-124">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="14a08-125">Aşağıdaki tabloda ve için desteklenen birleşimler gösterilmektedir `rclsid` `riid` .</span><span class="sxs-lookup"><span data-stu-id="14a08-125">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="14a08-126">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="14a08-126">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="14a08-127">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="14a08-127">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="14a08-128">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="14a08-128">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="14a08-129">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="14a08-129">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="14a08-130">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="14a08-130">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="14a08-131">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="14a08-131">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="14a08-132">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="14a08-132">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="14a08-133">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="14a08-133">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="14a08-134">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="14a08-134">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="14a08-135">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="14a08-135">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="14a08-136">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="14a08-136">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="14a08-137">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="14a08-137">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="14a08-138">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="14a08-138">CLSID_CLRStrongName</span></span>|<span data-ttu-id="14a08-139">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="14a08-139">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14a08-140">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14a08-140">Requirements</span></span>  

 <span data-ttu-id="14a08-141">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14a08-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14a08-142">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="14a08-142">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="14a08-143">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="14a08-143">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14a08-144">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14a08-144">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14a08-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14a08-145">See also</span></span>

- [<span data-ttu-id="14a08-146">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14a08-146">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="14a08-147">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="14a08-147">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="14a08-148">Hosting</span><span class="sxs-lookup"><span data-stu-id="14a08-148">Hosting</span></span>](index.md)
