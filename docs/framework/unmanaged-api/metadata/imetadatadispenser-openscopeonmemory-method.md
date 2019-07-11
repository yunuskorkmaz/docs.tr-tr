---
title: IMetaDataDispenser::OpenScopeOnMemory Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 204e5660e95434f8d0c44d54f4fdbb1c2acc1e5d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777779"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="78f4f-102">IMetaDataDispenser::OpenScopeOnMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f4f-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="78f4f-103">Var olan meta veriler içeren belleği açılır.</span><span class="sxs-lookup"><span data-stu-id="78f4f-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="78f4f-104">Diğer bir deyişle, bu yöntem, var olan verilere meta veri olarak kabul edilir bellek belirtilen bir alan açılır.</span><span class="sxs-lookup"><span data-stu-id="78f4f-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f4f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78f4f-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78f4f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="78f4f-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="78f4f-107">[in] Bellek alanı başlangıç adresini belirten bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="78f4f-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="78f4f-108">[in] Bellek alanının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="78f4f-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="78f4f-109">[in] Değerini [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) açmak için (okuma, yazma ve benzeri) modunu belirtmek için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="78f4f-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="78f4f-110">[in] Döndürülecek istenen meta veri arayüzü Laboratuvardaki; çağıran, (okuma) alma ya da (yazma) meta verileri yayma arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="78f4f-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="78f4f-111">Değerini `riid` "Al" veya "Yayımla" arabirimlerinden birini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="78f4f-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="78f4f-112">IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2 değerler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="78f4f-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="78f4f-113">[out] Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="78f4f-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78f4f-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78f4f-114">Remarks</span></span>  
 <span data-ttu-id="78f4f-115">Bellek içi kopyayı meta verilerin yöntemleri "Al" arabirimlerinden birini kullanarak veya eklenen "Yayımla" arabirimleri birinden yöntemleri kullanarak sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="78f4f-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="78f4f-116">`OpenScopeOnMemory` Yöntemi benzer [Imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) yöntemi dışında meta veriler ilgi bellek yerine bir dosya diskte zaten mevcut.</span><span class="sxs-lookup"><span data-stu-id="78f4f-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="78f4f-117">Ortak dil çalışma zamanı (CLR) meta verileri, bellek, hedef alan içermiyorsa `OpenScopeOnMemory` yöntemi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="78f4f-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78f4f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78f4f-118">Requirements</span></span>  
 <span data-ttu-id="78f4f-119">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78f4f-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78f4f-120">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="78f4f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78f4f-121">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="78f4f-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="78f4f-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78f4f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f4f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78f4f-123">See also</span></span>

- [<span data-ttu-id="78f4f-124">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78f4f-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="78f4f-125">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78f4f-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="78f4f-126">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78f4f-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="78f4f-127">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78f4f-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="78f4f-128">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78f4f-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="78f4f-129">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78f4f-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="78f4f-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78f4f-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="78f4f-131">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78f4f-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
