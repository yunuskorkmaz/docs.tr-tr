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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4c6a9473a698e4635c8b5cc9fb58963334dfd65e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081800"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="e027b-102">IMetaDataInfo::GetFileMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e027b-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="e027b-103">Eşleşen dosya ve tür eşlemesi bellek bölgesini alır.</span><span class="sxs-lookup"><span data-stu-id="e027b-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e027b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e027b-104">Syntax</span></span>  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e027b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e027b-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="e027b-106">[out] Eşleşen dosya başlangıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e027b-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="e027b-107">[out] Eşleştirilmiş bölge boyutu.</span><span class="sxs-lookup"><span data-stu-id="e027b-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="e027b-108">Varsa `pdwMappingType` olduğu `fmFlat`, dosyanın boyutu budur.</span><span class="sxs-lookup"><span data-stu-id="e027b-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="e027b-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) eşleme türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="e027b-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="e027b-110">Ortak dil çalışma zamanı (CLR) her zaman geçerli uygulamasını döndürür `fmFlat`.</span><span class="sxs-lookup"><span data-stu-id="e027b-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="e027b-111">Diğer değerleri, gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e027b-111">Other values are reserved for future use.</span></span> <span data-ttu-id="e027b-112">Ancak, diğer değerleri gelecek sürümlerde etkinleştirilmemiş olabilir veya yayınlar hizmet için döndürülen değer her zaman doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e027b-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e027b-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e027b-113">Return Value</span></span>  
  
|<span data-ttu-id="e027b-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e027b-114">HRESULT</span></span>|<span data-ttu-id="e027b-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e027b-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e027b-116">Tüm çıktıların doldurulur.</span><span class="sxs-lookup"><span data-stu-id="e027b-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="e027b-117">NULL bir bağımsız değişken değeri geçirildi.</span><span class="sxs-lookup"><span data-stu-id="e027b-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="e027b-118">CLR uygulamasındaki bellek bölge bilgileri sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="e027b-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="e027b-119">Bu durum aşağıdaki nedenlerden dolayı oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="e027b-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="e027b-120">-Meta veri kapsamı ile açılmış `ofWrite` veya `ofCopyMemory` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="e027b-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="e027b-121">-Meta veri kapsamı olmadan açılmış `ofReadOnly` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="e027b-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="e027b-122">- [Imetadatadispenser::openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) yöntemi yalnızca dosya meta veri bölümü açmak için kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="e027b-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="e027b-123">-Dosya taşınabilir çalıştırılabilir (PE) dosyası değil.</span><span class="sxs-lookup"><span data-stu-id="e027b-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="e027b-124">**Not:**  Bu koşullar CLR uygulamasının bağlıdır ve gelecek sürümleri CLR'nin zayıflar muhtemeldir.</span><span class="sxs-lookup"><span data-stu-id="e027b-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e027b-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e027b-125">Remarks</span></span>  
 <span data-ttu-id="e027b-126">Bellek, `ppvData` noktalarına, temel alınan meta veri kapsamı yalnızca açık olduğu sürece geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e027b-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="e027b-127">Bu yöntemi çağırarak bir diskteki dosyanın meta verilerini belleğe eşlediğinizde, iş için sırayla [Imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) yöntemi belirtmelisiniz `ofReadOnly` bayrağı ve değil belirtmelisiniz `ofWrite` veya `ofCopyMemory` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="e027b-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="e027b-128">Her kapsam için dosya eşleme türü seçimi, CLR'nin belirli bir uygulamaya özeldir.</span><span class="sxs-lookup"><span data-stu-id="e027b-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="e027b-129">Kullanıcı tarafından ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="e027b-129">It cannot be set by the user.</span></span> <span data-ttu-id="e027b-130">Her zaman geçerli uygulama CLR döndürür `fmFlat` içinde `pdwMappingType`, ancak gelecekte CLR'nin sürümünü veya gelecek hizmet sürümlerini belirli bir sürümü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e027b-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="e027b-131">Döndürülen değer her zaman iade etmelisiniz `pdwMappingType`, farklı alan farklı düzenler ve ofsetleri olduğundan.</span><span class="sxs-lookup"><span data-stu-id="e027b-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="e027b-132">Herhangi bir üç parametre için NULL geçirme desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e027b-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="e027b-133">Yöntem döndürür `E_INVALIDARG`, ve çıkışları hiçbiri doldurulur.</span><span class="sxs-lookup"><span data-stu-id="e027b-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="e027b-134">Eşleme türü veya bölgenin boyutunu yoksayılıyor anormal program sonlandırmada neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e027b-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e027b-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e027b-135">Requirements</span></span>  
 <span data-ttu-id="e027b-136">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e027b-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e027b-137">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="e027b-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e027b-138">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="e027b-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e027b-139">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e027b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e027b-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e027b-140">See also</span></span>

- [<span data-ttu-id="e027b-141">IMetaDataInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e027b-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [<span data-ttu-id="e027b-142">CorFileMapping Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e027b-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
