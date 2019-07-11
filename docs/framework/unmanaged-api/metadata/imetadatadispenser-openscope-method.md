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
ms.openlocfilehash: 6e157c758b472ea89e21c1ed1ba8c17693c20a3d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777796"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="3cad9-102">IMetaDataDispenser::OpenScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3cad9-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="3cad9-103">Var olan ve disk üzerindeki bir dosya açılır ve meta verileri belleğe eşler.</span><span class="sxs-lookup"><span data-stu-id="3cad9-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cad9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3cad9-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cad9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3cad9-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="3cad9-106">[in] Açılması için dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="3cad9-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="3cad9-107">Dosyanın ortak dil çalışma zamanı (CLR) meta verileri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="3cad9-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="3cad9-108">[in] Değerini [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) açmak için (okuma, yazma ve benzeri) modunu belirtmek için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="3cad9-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="3cad9-109">[in] Döndürülecek istenen meta veri arayüzü Laboratuvardaki; çağıran, (okuma) alma ya da (yazma) meta verileri yayma arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3cad9-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="3cad9-110">Değerini `riid` "Al" veya "Yayımla" arabirimlerinden birini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3cad9-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="3cad9-111">IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2 değerler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3cad9-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="3cad9-112">[out] Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3cad9-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cad9-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3cad9-113">Remarks</span></span>  
 <span data-ttu-id="3cad9-114">Bellek içi kopyayı meta verilerin yöntemleri "Al" arabirimlerinden birini kullanarak veya eklenen "Yayımla" arabirimleri birinden yöntemleri kullanarak sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3cad9-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="3cad9-115">Hedef dosyanın CLR meta veriler içermiyorsa `OpenScope` yöntemi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3cad9-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="3cad9-116">.NET Framework sürüm 1.0 ve sürüm 1.1, bir kapsam ise açıldığında ile `dwOpenFlags` için ofRead ayarlanırsa, bunu paylaşmak için uygundur.</span><span class="sxs-lookup"><span data-stu-id="3cad9-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="3cad9-117">Diğer bir deyişle, varsa sonraki çağrılar `OpenScope` oluşturdular. daha önce açıldı bir dosya, var olan kapsamı yeniden ve yeni bir veri yapılarını kümesi oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="3cad9-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="3cad9-118">Ancak, sorunlar, bu paylaşım nedeniyle ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="3cad9-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="3cad9-119">.NET Framework sürüm 2. 0'da, kapsamları ile açılır. `dwOpenFlags` ofRead kümesine artık paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="3cad9-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="3cad9-120">Paylaşılan kapsam için ofReadOnly değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="3cad9-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="3cad9-121">Bir kapsam paylaşıldığında "meta veri arabirimleri okuma/yazma" kullanan sorguları başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3cad9-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cad9-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3cad9-122">Requirements</span></span>  
 <span data-ttu-id="3cad9-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cad9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cad9-124">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3cad9-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3cad9-125">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="3cad9-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3cad9-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cad9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cad9-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cad9-127">See also</span></span>

- [<span data-ttu-id="3cad9-128">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3cad9-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="3cad9-129">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cad9-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="3cad9-130">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cad9-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="3cad9-131">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cad9-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="3cad9-132">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cad9-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3cad9-133">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cad9-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="3cad9-134">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cad9-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3cad9-135">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cad9-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
