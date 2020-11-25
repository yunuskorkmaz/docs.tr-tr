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
ms.openlocfilehash: 26293e38a275ca691c7d48dceb12c1e7dd316536
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713424"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="397ed-102">IMetaDataDispenser::OpenScopeOnMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="397ed-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>

<span data-ttu-id="397ed-103">Mevcut meta verileri içeren bir bellek alanını açar.</span><span class="sxs-lookup"><span data-stu-id="397ed-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="397ed-104">Diğer bir deyişle, bu yöntem mevcut verilerin meta veri olarak değerlendirilme belirtilen bir bellek alanını açar.</span><span class="sxs-lookup"><span data-stu-id="397ed-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="397ed-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="397ed-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="397ed-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="397ed-106">Parameters</span></span>  

 `pData`  
 <span data-ttu-id="397ed-107">'ndaki Bellek alanının başlangıç adresini belirten bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="397ed-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="397ed-108">'ndaki Bellek alanının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="397ed-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="397ed-109">'ndaki Açma için modu (okuma, yazma, vb.) belirtmek için [CorOpenFlags](coropenflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="397ed-109">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="397ed-110">'ndaki Döndürülecek istenen meta veri arabiriminin IID 'si; çağıran, meta verileri içeri aktarmak (okumak) veya yayma (yazmak) için arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="397ed-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="397ed-111">Değeri, `riid` "import" veya "yayma" arabirimlerinden birini belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="397ed-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="397ed-112">Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="397ed-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="397ed-113">dışı Döndürülen arabirime yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="397ed-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="397ed-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="397ed-114">Remarks</span></span>  

 <span data-ttu-id="397ed-115">Meta verilerin bellek içi kopyası, "içeri aktarma" arabirimlerinden birindeki yöntemler kullanılarak sorgulanabilir veya "yayma" arabirimlerinden birindeki yöntemleri kullanarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="397ed-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="397ed-116">`OpenScopeOnMemory`Yöntemi [ımetadatadağıtıcı:: OpenScope](imetadatadispenser-openscope-method.md) yöntemine benzerdir, ancak ilgilendiğiniz meta veriler disk üzerindeki bir dosya yerine bellekte zaten mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="397ed-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="397ed-117">Belleğin hedef alanı ortak dil çalışma zamanı (CLR) meta verileri içermiyorsa, `OpenScopeOnMemory` Yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="397ed-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="397ed-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="397ed-118">Requirements</span></span>  

 <span data-ttu-id="397ed-119">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="397ed-119">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="397ed-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="397ed-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="397ed-121">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="397ed-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="397ed-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="397ed-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="397ed-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="397ed-123">See also</span></span>

- [<span data-ttu-id="397ed-124">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="397ed-124">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="397ed-125">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="397ed-125">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="397ed-126">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="397ed-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="397ed-127">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="397ed-127">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="397ed-128">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="397ed-128">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="397ed-129">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="397ed-129">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="397ed-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="397ed-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="397ed-131">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="397ed-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
