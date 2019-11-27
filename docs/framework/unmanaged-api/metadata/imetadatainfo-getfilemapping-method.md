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
ms.openlocfilehash: 0cd2071d4410615a08e774ba30e0e8fe8d1fa7c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436182"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="89867-102">IMetaDataInfo::GetFileMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89867-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="89867-103">Eşlenen dosyanın bellek bölgesini ve eşleme türünü alır.</span><span class="sxs-lookup"><span data-stu-id="89867-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89867-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89867-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89867-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89867-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="89867-106">dışı Eşlenen dosyanın başlangıcına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="89867-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="89867-107">dışı Eşlenen bölgenin boyutu.</span><span class="sxs-lookup"><span data-stu-id="89867-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="89867-108">`pdwMappingType` `fmFlat`, bu dosyanın boyutudur.</span><span class="sxs-lookup"><span data-stu-id="89867-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="89867-109">dışı Eşleme türünü gösteren [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="89867-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="89867-110">Ortak dil çalışma zamanının (CLR) geçerli uygulanması her zaman `fmFlat`döndürür.</span><span class="sxs-lookup"><span data-stu-id="89867-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="89867-111">Diğer değerler gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="89867-111">Other values are reserved for future use.</span></span> <span data-ttu-id="89867-112">Bununla birlikte, döndürülen değeri her zaman doğrulamanız gerekir, çünkü diğer değerler gelecek sürümlerde veya hizmet sürümlerinde etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="89867-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89867-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="89867-113">Return Value</span></span>  
  
|<span data-ttu-id="89867-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89867-114">HRESULT</span></span>|<span data-ttu-id="89867-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89867-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="89867-116">Tüm çıkışlar doldurulur.</span><span class="sxs-lookup"><span data-stu-id="89867-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="89867-117">NULL bir bağımsız değişken değeri olarak geçirildi.</span><span class="sxs-lookup"><span data-stu-id="89867-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="89867-118">CLR uygulama bellek bölgesi hakkında bilgi sağlayamıyor.</span><span class="sxs-lookup"><span data-stu-id="89867-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="89867-119">Bu durum aşağıdaki nedenlerden kaynaklanabilir:</span><span class="sxs-lookup"><span data-stu-id="89867-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="89867-120">-Meta veri kapsamı `ofWrite` veya `ofCopyMemory` bayrağıyla açıldı.</span><span class="sxs-lookup"><span data-stu-id="89867-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="89867-121">-Meta veri kapsamı `ofReadOnly` bayrağı olmadan açıldı.</span><span class="sxs-lookup"><span data-stu-id="89867-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="89867-122">-Dosyanın yalnızca meta veri bölümünü açmak için [ımetadatadağıtıcı:: OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) yöntemi kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="89867-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="89867-123">-Dosya taşınabilir bir çalıştırılabilir (PE) dosyası değil.</span><span class="sxs-lookup"><span data-stu-id="89867-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="89867-124">**Note:**  Bu koşullar CLR uygulamasına Bağımlıdır ve CLR 'nin gelecek sürümlerinde zayıflatılmış olma olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="89867-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89867-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89867-125">Remarks</span></span>  
 <span data-ttu-id="89867-126">`ppvData`, işaret eden bellek yalnızca temeldeki meta veri kapsamı açık olduğu sürece geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="89867-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="89867-127">Bu yöntemin çalışması için, [ımetadatadağıtıcı:: OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metodunu çağırarak disk üzerindeki bir dosyanın meta verilerini belleğe eşlediğinizde `ofReadOnly` bayrağını belirtmeniz gerekir ve `ofWrite` veya `ofCopyMemory` bayrağını belirtmemelidir.</span><span class="sxs-lookup"><span data-stu-id="89867-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="89867-128">Her kapsam için dosya eşleme türü seçimi, CLR 'nin belirli bir uygulamasına özgüdür.</span><span class="sxs-lookup"><span data-stu-id="89867-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="89867-129">Kullanıcı tarafından ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="89867-129">It cannot be set by the user.</span></span> <span data-ttu-id="89867-130">CLR 'nin geçerli uygulanması her zaman `pdwMappingType``fmFlat` döndürür, ancak bu, CLR 'nin gelecekteki sürümlerinde veya belirli bir sürümün gelecekteki hizmet sürümlerinde değişebilir.</span><span class="sxs-lookup"><span data-stu-id="89867-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="89867-131">Farklı türlerin farklı düzenlerine ve uzaklıklara sahip olacağı için `pdwMappingType`döndürülen değeri her zaman denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="89867-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="89867-132">Üç parametreden herhangi biri için NULL geçirme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="89867-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="89867-133">Yöntemi `E_INVALIDARG`döndürür ve çıktıların hiçbiri doldurulmaz.</span><span class="sxs-lookup"><span data-stu-id="89867-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="89867-134">Eşleme türü yok sayılıyor veya bölgenin boyutu olağan dışı program sonlandırmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="89867-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89867-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89867-135">Requirements</span></span>  
 <span data-ttu-id="89867-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89867-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89867-137">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="89867-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89867-138">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="89867-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89867-139">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89867-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89867-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89867-140">See also</span></span>

- [<span data-ttu-id="89867-141">IMetaDataInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89867-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [<span data-ttu-id="89867-142">CorFileMapping Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="89867-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
