---
title: "IMetaDataDispenser::OpenScopeOnMemory Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser.OpenScopeOnMemory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0c6cfc21a5aecfc043a7720959610210df1d15ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="8aca1-102">IMetaDataDispenser::OpenScopeOnMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8aca1-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="8aca1-103">Var olan meta veriler içeren bellek alanı açılır.</span><span class="sxs-lookup"><span data-stu-id="8aca1-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="8aca1-104">Diğer bir deyişle, bu yöntem belirtilen alan var olan verileri meta verileri kabul edilir bellek açar.</span><span class="sxs-lookup"><span data-stu-id="8aca1-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aca1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8aca1-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8aca1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8aca1-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="8aca1-107">[in] Bellek alanının başlangıç adresini belirtir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8aca1-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="8aca1-108">[in] Bellek alanının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="8aca1-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="8aca1-109">[in] Değerini [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırması (okuma, yazma ve benzeri) modunu açmak için belirtin.</span><span class="sxs-lookup"><span data-stu-id="8aca1-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="8aca1-110">[in] Döndürülecek istenen meta veri arabirimi IID; Arayan (okuma) almak veya (yazma) meta veri yayma arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8aca1-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="8aca1-111">Değeri `riid` "Al" veya "Yayımla" arabirimleri birini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8aca1-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="8aca1-112">Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2 arasındadır.</span><span class="sxs-lookup"><span data-stu-id="8aca1-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="8aca1-113">[out] Döndürülen arabirimi yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8aca1-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8aca1-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8aca1-114">Remarks</span></span>  
 <span data-ttu-id="8aca1-115">Bellek içi kopya meta verilerin "alma" arabirimleri birinden yöntemleri kullanarak ya da "Yayımla" arabirimleri birinden yöntemleri kullanarak eklenen sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="8aca1-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="8aca1-116">`OpenScopeOnMemory` Yöntemi benzer [Imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) yöntemi, meta verileri ilgi bellek yerine disk üzerindeki bir dosya zaten var ancak bu.</span><span class="sxs-lookup"><span data-stu-id="8aca1-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="8aca1-117">Hedef alan bellek ortak dil çalışma zamanı (CLR) meta verileri, içermiyorsa `OpenScopeOnMemory` yöntemi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="8aca1-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aca1-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8aca1-118">Requirements</span></span>  
 <span data-ttu-id="8aca1-119">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aca1-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aca1-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8aca1-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8aca1-121">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8aca1-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8aca1-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aca1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aca1-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8aca1-123">See Also</span></span>  
 [<span data-ttu-id="8aca1-124">Imetadatadispenser arabirimi</span><span class="sxs-lookup"><span data-stu-id="8aca1-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="8aca1-125">Imetadatadispenserex arabirimi</span><span class="sxs-lookup"><span data-stu-id="8aca1-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="8aca1-126">Imetadataassemblyemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="8aca1-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="8aca1-127">Imetadataassemblyımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="8aca1-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="8aca1-128">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="8aca1-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="8aca1-129">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8aca1-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="8aca1-130">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="8aca1-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="8aca1-131">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8aca1-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
