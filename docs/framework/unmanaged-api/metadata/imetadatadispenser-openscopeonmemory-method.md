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
ms.openlocfilehash: 492c37540ad68b5b134520218eedc59013c68519
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175934"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="afa5f-102">IMetaDataDispenser::OpenScopeOnMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="afa5f-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="afa5f-103">Varolan meta verileri içeren bir bellek alanı açar.</span><span class="sxs-lookup"><span data-stu-id="afa5f-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="afa5f-104">Diğer bir deyişle, bu yöntem, varolan verilerin meta veri olarak kabul edildiği belirli bir bellek alanını açar.</span><span class="sxs-lookup"><span data-stu-id="afa5f-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afa5f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="afa5f-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afa5f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="afa5f-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="afa5f-107">[içinde] Bellek alanının başlangıç adresini belirten bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="afa5f-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="afa5f-108">[içinde] Bellek alanının boyutu, baytlar halinde.</span><span class="sxs-lookup"><span data-stu-id="afa5f-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="afa5f-109">[içinde] Açılış kipini (okuma, yazma vb.) belirtmek için [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırmasının değeri.</span><span class="sxs-lookup"><span data-stu-id="afa5f-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="afa5f-110">[içinde] Döndürülecek istenilen meta veri arabiriminin IID'si; arayan, meta verileri almak (okumak) veya yayacak (yazmak) için arabirimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="afa5f-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="afa5f-111">Değeri "içe aktarma" veya "yayış" arabirimlerinden birini `riid` belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="afa5f-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="afa5f-112">Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="afa5f-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="afa5f-113">[çıkış] Döndürülen arabirimin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="afa5f-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afa5f-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="afa5f-114">Remarks</span></span>  
 <span data-ttu-id="afa5f-115">Meta verilerin bellek içi kopyası ,"alma" arabirimlerinden birinden yöntemler kullanılarak sorgulanabilir veya "yaslamak" arabirimlerinden yöntemler kullanılarak sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="afa5f-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="afa5f-116">`OpenScopeOnMemory` Yöntem, [iMetaDataDispenser'a benzer::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) yöntemi, ilgi meta verilerinin diskteki bir dosya yerine bellekte zaten var olması dışında.</span><span class="sxs-lookup"><span data-stu-id="afa5f-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="afa5f-117">Bellek hedef alanı ortak dil çalışma zamanı (CLR) meta `OpenScopeOnMemory` verileri içermiyorsa, yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="afa5f-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afa5f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="afa5f-118">Requirements</span></span>  
 <span data-ttu-id="afa5f-119">**Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afa5f-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afa5f-120">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="afa5f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="afa5f-121">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="afa5f-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="afa5f-122">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afa5f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa5f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afa5f-123">See also</span></span>

- [<span data-ttu-id="afa5f-124">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="afa5f-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="afa5f-125">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afa5f-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="afa5f-126">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afa5f-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="afa5f-127">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afa5f-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="afa5f-128">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afa5f-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="afa5f-129">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afa5f-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="afa5f-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afa5f-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="afa5f-131">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afa5f-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
