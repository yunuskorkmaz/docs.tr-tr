---
title: IMetaDataDispenser::OpenScope Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0fb805e3292d90fd5f9562d9b0b8fcc31f84ec7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449370"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="779b6-102">IMetaDataDispenser::OpenScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="779b6-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="779b6-103">Var olan, disk üzerindeki bir dosyayı açar ve belleğe meta verilerini eşler.</span><span class="sxs-lookup"><span data-stu-id="779b6-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="779b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="779b6-104">Syntax</span></span>  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="779b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="779b6-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="779b6-106">[in] Açılması için dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="779b6-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="779b6-107">Ortak dil çalışma zamanı (CLR) meta veri dosyası içermelidir.</span><span class="sxs-lookup"><span data-stu-id="779b6-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="779b6-108">[in] Değerini [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırması (okuma, yazma ve benzeri) modunu açmak için belirtin.</span><span class="sxs-lookup"><span data-stu-id="779b6-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="779b6-109">[in] Döndürülecek istenen meta veri arabirimi IID; Arayan (okuma) almak veya (yazma) meta veri yayma arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="779b6-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="779b6-110">Değeri `riid` "Al" veya "Yayımla" arabirimleri birini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="779b6-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="779b6-111">Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2 arasındadır.</span><span class="sxs-lookup"><span data-stu-id="779b6-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="779b6-112">[out] Döndürülen arabirimi yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="779b6-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="779b6-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="779b6-113">Remarks</span></span>  
 <span data-ttu-id="779b6-114">Bellek içi kopya meta verilerin "alma" arabirimleri birinden yöntemleri kullanarak ya da "Yayımla" arabirimleri birinden yöntemleri kullanarak eklenen sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="779b6-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="779b6-115">Hedef dosya CLR meta verileri, içermiyorsa `OpenScope` yöntemi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="779b6-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="779b6-116">.NET Framework sürüm 1.0 ve sürüm 1.1, kapsam, açıldığında ile `dwOpenFlags` ofRead için ayarlanırsa, bu paylaşım için uygundur.</span><span class="sxs-lookup"><span data-stu-id="779b6-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="779b6-117">Diğer bir deyişle, sonraki varsa çağrılar `OpenScope` geçişi daha önce açıldı bir dosya adına, varolan bir kapsamın yeniden ve veri yapıları yeni bir dizi oluşturulmadı.</span><span class="sxs-lookup"><span data-stu-id="779b6-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="779b6-118">Ancak, sorunlar, bu paylaşımı nedeniyle ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="779b6-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="779b6-119">.NET Framework sürüm 2. 0'da, kapsamları açılmış `dwOpenFlags` ofRead kümesine artık paylaşılan.</span><span class="sxs-lookup"><span data-stu-id="779b6-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="779b6-120">Paylaşılan kapsam izin vermek için ofReadOnly değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="779b6-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="779b6-121">Bir kapsam paylaşıldığında, "meta veri arabirimleri okuma/yazma" kullanan sorguları başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="779b6-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="779b6-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="779b6-122">Requirements</span></span>  
 <span data-ttu-id="779b6-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="779b6-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="779b6-124">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="779b6-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="779b6-125">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="779b6-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="779b6-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="779b6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="779b6-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="779b6-127">See Also</span></span>  
 [<span data-ttu-id="779b6-128">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="779b6-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="779b6-129">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="779b6-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="779b6-130">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="779b6-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="779b6-131">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="779b6-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="779b6-132">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="779b6-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="779b6-133">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="779b6-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="779b6-134">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="779b6-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="779b6-135">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="779b6-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
