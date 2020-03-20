---
title: IMetaDataInfo::GetFileMapping Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
ms.openlocfilehash: 0f5bdf97132c05e765cd6fa423a19bb996105d28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175271"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="1df64-102">IMetaDataInfo::GetFileMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1df64-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="1df64-103">Eşlenen dosyanın bellek bölgesini ve eşleme türünü alır.</span><span class="sxs-lookup"><span data-stu-id="1df64-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1df64-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1df64-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1df64-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1df64-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="1df64-106">[çıkış] Eşlenen dosyanın başlangıcına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1df64-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="1df64-107">[çıkış] Eşlenen bölgenin boyutu.</span><span class="sxs-lookup"><span data-stu-id="1df64-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="1df64-108">`pdwMappingType` Varsa, `fmFlat`bu dosyanın boyutudur.</span><span class="sxs-lookup"><span data-stu-id="1df64-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="1df64-109">[çıkış] Eşleme türünü gösteren [bir CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="1df64-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="1df64-110">Ortak dil çalışma zamanı (CLR) geçerli `fmFlat`uygulama her zaman döndürür.</span><span class="sxs-lookup"><span data-stu-id="1df64-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="1df64-111">Diğer değerler ileride kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1df64-111">Other values are reserved for future use.</span></span> <span data-ttu-id="1df64-112">Ancak, diğer değerler gelecekteki sürümlerde veya hizmet sürümlerinde etkinleştirilebileceğinden, döndürülen değeri her zaman doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1df64-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1df64-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1df64-113">Return Value</span></span>  
  
|<span data-ttu-id="1df64-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1df64-114">HRESULT</span></span>|<span data-ttu-id="1df64-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1df64-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1df64-116">Tüm çıktılar doldurulur.</span><span class="sxs-lookup"><span data-stu-id="1df64-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="1df64-117">NULL bağımsız değişken değeri olarak geçirildi.</span><span class="sxs-lookup"><span data-stu-id="1df64-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="1df64-118">CLR uygulaması bellek bölgesi hakkında bilgi sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="1df64-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="1df64-119">Bu aşağıdaki nedenlerle olabilir:</span><span class="sxs-lookup"><span data-stu-id="1df64-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="1df64-120">- Meta veri kapsamı `ofWrite` veya `ofCopyMemory` bayrak ile açıldı.</span><span class="sxs-lookup"><span data-stu-id="1df64-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="1df64-121">- Meta veri kapsamı `ofReadOnly` bayrak olmadan açıldı.</span><span class="sxs-lookup"><span data-stu-id="1df64-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="1df64-122">- Dosyanın yalnızca meta veri bölümünü açmak için [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) yöntemi kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1df64-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="1df64-123">- Dosya taşınabilir bir yürütülebilir (PE) dosya değildir.</span><span class="sxs-lookup"><span data-stu-id="1df64-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="1df64-124">**Not:**  Bu koşullar CLR uygulamasına bağlıdır ve CLR'nin gelecekteki sürümlerinde zayıflamış olma olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="1df64-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1df64-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1df64-125">Remarks</span></span>  
 <span data-ttu-id="1df64-126">Yalnızca temel `ppvData` meta veri kapsamı açık olduğu sürece işaret eden bellek geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1df64-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="1df64-127">Bu yöntemin işe yaraması için, bir disk dosyasının meta verilerini [IMetaDataDispenser'ı](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) arayarak belleğe eşlediğinizde::OpenScope yöntemi, `ofReadOnly` bayrağı belirtmeniz gerekir ve bayrağı `ofWrite` belirtmemelisiniz. `ofCopyMemory`</span><span class="sxs-lookup"><span data-stu-id="1df64-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="1df64-128">Her kapsam için dosya eşleme türü seçimi CLR belirli bir uygulamaya özgüdür.</span><span class="sxs-lookup"><span data-stu-id="1df64-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="1df64-129">Kullanıcı tarafından ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="1df64-129">It cannot be set by the user.</span></span> <span data-ttu-id="1df64-130">CLR'nin geçerli uygulaması `fmFlat` her `pdwMappingType`zaman , ancak bu CLR'nin gelecekteki sürümlerinde veya belirli bir sürümün gelecekteki hizmet sürümlerinde değişebilir.</span><span class="sxs-lookup"><span data-stu-id="1df64-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="1df64-131">Farklı türlerde farklı düzenler `pdwMappingType`ve uzaklıklar olacağından, iade edilen değeri her zaman denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1df64-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="1df64-132">Üç parametreden herhangi biri için NULL'u geçmek desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="1df64-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="1df64-133">Yöntem döndürür `E_INVALIDARG`ve çıktıların hiçbiri doldurulur.</span><span class="sxs-lookup"><span data-stu-id="1df64-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="1df64-134">Eşleme türünü veya bölgenin boyutunu yok saymak anormal program sonlandırmaneden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1df64-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1df64-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1df64-135">Requirements</span></span>  
 <span data-ttu-id="1df64-136">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1df64-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1df64-137">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1df64-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1df64-138">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1df64-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1df64-139">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1df64-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1df64-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1df64-140">See also</span></span>

- [<span data-ttu-id="1df64-141">IMetaDataInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1df64-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [<span data-ttu-id="1df64-142">CorFileMapping Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="1df64-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
