---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatadağıtıcı:: OpenScopeOnMemory Yöntemi'
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
ms.openlocfilehash: 589c68ab60eec55efc43d077807789e75ae1682f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753594"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="e6b9c-103">IMetaDataDispenser::OpenScopeOnMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6b9c-103">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>

<span data-ttu-id="e6b9c-104">Mevcut meta verileri içeren bir bellek alanını açar.</span><span class="sxs-lookup"><span data-stu-id="e6b9c-104">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="e6b9c-105">Diğer bir deyişle, bu yöntem mevcut verilerin meta veri olarak değerlendirilme belirtilen bir bellek alanını açar.</span><span class="sxs-lookup"><span data-stu-id="e6b9c-105">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b9c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6b9c-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6b9c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6b9c-107">Parameters</span></span>  

 `pData`  
 <span data-ttu-id="e6b9c-108">'ndaki Bellek alanının başlangıç adresini belirten bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e6b9c-108">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="e6b9c-109">'ndaki Bellek alanının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="e6b9c-109">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="e6b9c-110">'ndaki Açma için modu (okuma, yazma, vb.) belirtmek için [CorOpenFlags](coropenflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="e6b9c-110">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="e6b9c-111">'ndaki Döndürülecek istenen meta veri arabiriminin IID 'si; çağıran, meta verileri içeri aktarmak (okumak) veya yayma (yazmak) için arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6b9c-111">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="e6b9c-112">Değeri, `riid` "import" veya "yayma" arabirimlerinden birini belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="e6b9c-112">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="e6b9c-113">Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="e6b9c-113">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="e6b9c-114">dışı Döndürülen arabirime yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e6b9c-114">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6b9c-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6b9c-115">Remarks</span></span>  

 <span data-ttu-id="e6b9c-116">Meta verilerin bellek içi kopyası, "içeri aktarma" arabirimlerinden birindeki yöntemler kullanılarak sorgulanabilir veya "yayma" arabirimlerinden birindeki yöntemleri kullanarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e6b9c-116">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="e6b9c-117">`OpenScopeOnMemory`Yöntemi [ımetadatadağıtıcı:: OpenScope](imetadatadispenser-openscope-method.md) yöntemine benzerdir, ancak ilgilendiğiniz meta veriler disk üzerindeki bir dosya yerine bellekte zaten mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="e6b9c-117">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="e6b9c-118">Belleğin hedef alanı ortak dil çalışma zamanı (CLR) meta verileri içermiyorsa, `OpenScopeOnMemory` Yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e6b9c-118">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6b9c-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6b9c-119">Requirements</span></span>  

 <span data-ttu-id="e6b9c-120">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6b9c-120">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6b9c-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e6b9c-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e6b9c-122">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e6b9c-122">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e6b9c-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6b9c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6b9c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6b9c-124">See also</span></span>

- [<span data-ttu-id="e6b9c-125">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6b9c-125">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="e6b9c-126">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6b9c-126">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="e6b9c-127">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6b9c-127">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="e6b9c-128">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6b9c-128">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="e6b9c-129">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6b9c-129">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e6b9c-130">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6b9c-130">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="e6b9c-131">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6b9c-131">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e6b9c-132">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6b9c-132">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
