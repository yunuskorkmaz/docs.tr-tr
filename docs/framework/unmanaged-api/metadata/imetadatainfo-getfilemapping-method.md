---
description: ': IMetaDataInfo:: GetFileMapping yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 82a1a23c50a4d8340804f66966933fc6a11e0f8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688487"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="d957c-103">IMetaDataInfo::GetFileMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d957c-103">IMetaDataInfo::GetFileMapping Method</span></span>

<span data-ttu-id="d957c-104">Eşlenen dosyanın bellek bölgesini ve eşleme türünü alır.</span><span class="sxs-lookup"><span data-stu-id="d957c-104">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d957c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d957c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d957c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d957c-106">Parameters</span></span>  

 `ppvData`  
 <span data-ttu-id="d957c-107">dışı Eşlenen dosyanın başlangıcına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d957c-107">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="d957c-108">dışı Eşlenen bölgenin boyutu.</span><span class="sxs-lookup"><span data-stu-id="d957c-108">[out] The size of the mapped region.</span></span> <span data-ttu-id="d957c-109">`pdwMappingType`İse `fmFlat` , bu dosyanın boyutudur.</span><span class="sxs-lookup"><span data-stu-id="d957c-109">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="d957c-110">dışı Eşleme türünü gösteren [CorFileMapping](corfilemapping-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="d957c-110">[out] A [CorFileMapping](corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="d957c-111">Ortak dil çalışma zamanının (CLR) geçerli uygulanması her zaman döndürülür `fmFlat` .</span><span class="sxs-lookup"><span data-stu-id="d957c-111">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="d957c-112">Diğer değerler gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d957c-112">Other values are reserved for future use.</span></span> <span data-ttu-id="d957c-113">Bununla birlikte, döndürülen değeri her zaman doğrulamanız gerekir, çünkü diğer değerler gelecek sürümlerde veya hizmet sürümlerinde etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d957c-113">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d957c-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d957c-114">Return Value</span></span>  
  
|<span data-ttu-id="d957c-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d957c-115">HRESULT</span></span>|<span data-ttu-id="d957c-116">Description</span><span class="sxs-lookup"><span data-stu-id="d957c-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d957c-117">Tüm çıkışlar doldurulur.</span><span class="sxs-lookup"><span data-stu-id="d957c-117">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="d957c-118">NULL bir bağımsız değişken değeri olarak geçirildi.</span><span class="sxs-lookup"><span data-stu-id="d957c-118">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="d957c-119">CLR uygulama bellek bölgesi hakkında bilgi sağlayamıyor.</span><span class="sxs-lookup"><span data-stu-id="d957c-119">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="d957c-120">Bu durum aşağıdaki nedenlerden kaynaklanabilir:</span><span class="sxs-lookup"><span data-stu-id="d957c-120">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="d957c-121">-Meta veri kapsamı `ofWrite` veya `ofCopyMemory` bayrağıyla açıldı.</span><span class="sxs-lookup"><span data-stu-id="d957c-121">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="d957c-122">-Meta veri kapsamı bayrak olmadan açıldı `ofReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="d957c-122">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="d957c-123">-Dosyanın yalnızca meta veri bölümünü açmak için [ımetadatadağıtıcı:: OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) yöntemi kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="d957c-123">-   The [IMetaDataDispenser::OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="d957c-124">-Dosya taşınabilir bir çalıştırılabilir (PE) dosyası değil.</span><span class="sxs-lookup"><span data-stu-id="d957c-124">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="d957c-125">**Note:**  Bu koşullar CLR uygulamasına Bağımlıdır ve CLR 'nin gelecek sürümlerinde zayıflatılmış olma olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="d957c-125">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d957c-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d957c-126">Remarks</span></span>  

 <span data-ttu-id="d957c-127">' A işaret eden bellek `ppvData` yalnızca temeldeki meta veri kapsamı açık olduğu sürece geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d957c-127">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="d957c-128">Bu yöntemin çalışması için, [ımetadatadağıtıcı:: OpenScope](imetadatadispenser-openscope-method.md) metodunu çağırarak, disk üzerindeki bir dosyanın meta verilerini belleğe eşlediğinizde, bayrağını belirtmeniz gerekir `ofReadOnly` ve `ofWrite` veya bayrağını belirtmemelidir `ofCopyMemory` .</span><span class="sxs-lookup"><span data-stu-id="d957c-128">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="d957c-129">Her kapsam için dosya eşleme türü seçimi, CLR 'nin belirli bir uygulamasına özgüdür.</span><span class="sxs-lookup"><span data-stu-id="d957c-129">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="d957c-130">Kullanıcı tarafından ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="d957c-130">It cannot be set by the user.</span></span> <span data-ttu-id="d957c-131">CLR 'nin geçerli uygulanması her zaman ' `fmFlat` de döner `pdwMappingType` , ancak bu, clr 'nin gelecekteki sürümlerinde veya belirli bir sürümün gelecekteki hizmet sürümlerinde değişebilir.</span><span class="sxs-lookup"><span data-stu-id="d957c-131">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="d957c-132">`pdwMappingType`Farklı türlerin farklı düzenlerine ve uzaklıklara sahip olacağı için döndürülen değeri her zaman denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d957c-132">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="d957c-133">Üç parametreden herhangi biri için NULL geçirme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d957c-133">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="d957c-134">Yöntemi döndürülür `E_INVALIDARG` ve çıktıların hiçbiri doldurulmaz.</span><span class="sxs-lookup"><span data-stu-id="d957c-134">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="d957c-135">Eşleme türü yok sayılıyor veya bölgenin boyutu olağan dışı program sonlandırmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="d957c-135">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d957c-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d957c-136">Requirements</span></span>  

 <span data-ttu-id="d957c-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d957c-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d957c-138">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d957c-138">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d957c-139">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d957c-139">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d957c-140">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d957c-140">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d957c-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d957c-141">See also</span></span>

- [<span data-ttu-id="d957c-142">IMetaDataInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d957c-142">IMetaDataInfo Interface</span></span>](imetadatainfo-interface.md)
- [<span data-ttu-id="d957c-143">CorFileMapping Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d957c-143">CorFileMapping Enumeration</span></span>](corfilemapping-enumeration.md)
