---
title: IMetaDataInfo::GetFileMapping Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataInfo.GetFileMapping
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f974230dc5ddf2a663f05fc06850f49f1de6e773
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="0ddb4-102">IMetaDataInfo::GetFileMapping Metodu</span><span class="sxs-lookup"><span data-stu-id="0ddb4-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="0ddb4-103">Bellek bölge eşlenmiş dosyayı ve eşleme türü alır.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ddb4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ddb4-104">Syntax</span></span>  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ddb4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ddb4-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="0ddb4-106">[out] Bir işaretçi eşlenmiş dosyayı başlatma.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="0ddb4-107">[out] Eşlenen bölge boyutu.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="0ddb4-108">Varsa `pdwMappingType` olan `fmFlat`, dosya boyutudur.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="0ddb4-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) eşleme türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="0ddb4-110">Her zaman geçerli uygulama ortak dil çalışma zamanı (CLR) döndürür `fmFlat`.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="0ddb4-111">Diğer değerler, gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-111">Other values are reserved for future use.</span></span> <span data-ttu-id="0ddb4-112">Ancak, diğer değerler gelecek sürümlerde etkinleştirilebilir ya da sürümlerden hizmet için döndürülen değer her zaman doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ddb4-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0ddb4-113">Return Value</span></span>  
  
|<span data-ttu-id="0ddb4-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ddb4-114">HRESULT</span></span>|<span data-ttu-id="0ddb4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ddb4-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0ddb4-116">Tüm çıktıları doldurulur.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="0ddb4-117">NULL bir bağımsız değişken değeri iletildi.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="0ddb4-118">CLR uygulaması bellek bölge hakkında bilgi sağlayamıyor.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="0ddb4-119">Bu durum aşağıdaki nedenlerden ötürü oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="0ddb4-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="0ddb4-120">-Meta veri kapsamı ile açılmış `ofWrite` veya `ofCopyMemory` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="0ddb4-121">-Meta veri kapsamı olmadan açılmış `ofReadOnly` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="0ddb4-122">- [Imetadatadispenser::openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) yöntemi, dosyanın yalnızca meta veri bölümü açmak için kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="0ddb4-123">-Dosya taşınabilir yürütülebilir (PE) dosyası değil.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="0ddb4-124">**Not:** olması olası gelecekte CLR sürümlerini zayıflar olan ve bu koşullar CLR mantığınız bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ddb4-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ddb4-125">Remarks</span></span>  
 <span data-ttu-id="0ddb4-126">Bellek, `ppvData` sadece temel alınan meta veri kapsam açık olduğu sürece noktaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="0ddb4-127">Bu yöntemin çağırarak bir disk dosya meta verileri belleğe eşlediğinizde çalışmak sırayla [Imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) yöntemi, belirtmeniz gerekir `ofReadOnly` bayrağı ve değil belirtmelisiniz `ofWrite` veya `ofCopyMemory` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="0ddb4-128">Her kapsam için dosya eşleme türünün CLR belirli bir uygulama belirli seçimdir.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="0ddb4-129">Kullanıcı tarafından ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-129">It cannot be set by the user.</span></span> <span data-ttu-id="0ddb4-130">Her zaman geçerli uygulama CLR döndürür `fmFlat` içinde `pdwMappingType`, ancak CLR sürümleri veya gelecek hizmet sürümleri belirli bir sürümü gelecekte değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="0ddb4-131">Döndürülen değer her zaman kontrol `pdwMappingType`, farklı türler farklı düzenler ve uzaklıkları bulunduğundan.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="0ddb4-132">Üç parametrelerinden herhangi biri NULL geçirme desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="0ddb4-133">Yöntem `E_INVALIDARG`, ve çıkışları hiçbiri doldurulur.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="0ddb4-134">Eşleme türü veya bölge boyutunu yoksayılıyor anormal program sonlandırma neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ddb4-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ddb4-135">Requirements</span></span>  
 <span data-ttu-id="0ddb4-136">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ddb4-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ddb4-137">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0ddb4-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ddb4-138">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0ddb4-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ddb4-139">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ddb4-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ddb4-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ddb4-140">See Also</span></span>  
 [<span data-ttu-id="0ddb4-141">IMetaDataInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ddb4-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 [<span data-ttu-id="0ddb4-142">CorFileMapping Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="0ddb4-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
