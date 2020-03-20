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
ms.openlocfilehash: 5185fb6663910c85ce5dae1225b9b10c5dd8bb28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175947"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="25711-102">IMetaDataDispenser::OpenScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25711-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="25711-103">Varolan, diskteki bir dosyayı açar ve meta verilerini belleğe eşler.</span><span class="sxs-lookup"><span data-stu-id="25711-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25711-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25711-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25711-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25711-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="25711-106">[içinde] Açılacak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="25711-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="25711-107">Dosya ortak dil çalışma zamanı (CLR) meta verileri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="25711-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="25711-108">[içinde] Açılış kipini (okuma, yazma vb.) belirtmek için [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırmasının değeri.</span><span class="sxs-lookup"><span data-stu-id="25711-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="25711-109">[içinde] Döndürülecek istenilen meta veri arabiriminin IID'si; arayan, meta verileri almak (okumak) veya yayacak (yazmak) için arabirimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="25711-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="25711-110">Değeri "içe aktarma" veya "yayış" arabirimlerinden birini `riid` belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="25711-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="25711-111">Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="25711-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="25711-112">[çıkış] Döndürülen arabirimin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="25711-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25711-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25711-113">Remarks</span></span>  
 <span data-ttu-id="25711-114">Meta verilerin bellek içi kopyası ,"alma" arabirimlerinden birinden yöntemler kullanılarak sorgulanabilir veya "yaslamak" arabirimlerinden yöntemler kullanılarak sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="25711-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="25711-115">Hedef dosya CLR meta verileri içermiyorsa, `OpenScope` yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="25711-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="25711-116">.NET Framework sürüm 1.0 ve sürüm 1.1'de, `dwOpenFlags` ofRead'e ayarlı bir kapsam açılırsa, paylaşım için uygundur.</span><span class="sxs-lookup"><span data-stu-id="25711-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="25711-117">Diğer bir deyişle, `OpenScope` daha önce açılmış bir dosyanın adına sonraki çağrıları geçmek için, varolan kapsam yeniden kullanılır ve yeni bir veri yapıları kümesi oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="25711-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="25711-118">Ancak, sorunlar bu paylaşım nedeniyle ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="25711-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="25711-119">.NET Framework sürüm 2.0'da, `dwOpenFlags` ofRead'e ayarlı olarak açılan kapsamlar artık paylaşılmaz.</span><span class="sxs-lookup"><span data-stu-id="25711-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="25711-120">Kapsamın paylaşılmasına izin vermek için ReadOnly değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="25711-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="25711-121">Kapsam paylaşıldığında, "okuma/yazma" meta veri arabirimleri kullanan sorgular başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="25711-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25711-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25711-122">Requirements</span></span>  
 <span data-ttu-id="25711-123">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25711-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25711-124">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="25711-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25711-125">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="25711-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25711-126">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25711-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25711-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25711-127">See also</span></span>

- [<span data-ttu-id="25711-128">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25711-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="25711-129">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25711-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="25711-130">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25711-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="25711-131">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25711-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="25711-132">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25711-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="25711-133">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25711-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="25711-134">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25711-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="25711-135">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25711-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
