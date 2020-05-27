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
ms.openlocfilehash: 8d9de753f1c44338a96e990def80643d591f2a8b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007474"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="63502-102">IMetaDataDispenser::OpenScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63502-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="63502-103">Mevcut, disk üzerindeki bir dosyayı açar ve meta verilerini belleğe eşler.</span><span class="sxs-lookup"><span data-stu-id="63502-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63502-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="63502-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63502-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63502-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="63502-106">'ndaki Açılacak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="63502-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="63502-107">Dosya, ortak dil çalışma zamanı (CLR) meta verilerini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="63502-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="63502-108">'ndaki Açma için modu (okuma, yazma, vb.) belirtmek için [CorOpenFlags](coropenflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="63502-108">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="63502-109">'ndaki Döndürülecek istenen meta veri arabiriminin IID 'si; çağıran, meta verileri içeri aktarmak (okumak) veya yayma (yazmak) için arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="63502-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="63502-110">Değeri, `riid` "import" veya "yayma" arabirimlerinden birini belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="63502-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="63502-111">Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="63502-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="63502-112">dışı Döndürülen arabirime yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="63502-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63502-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63502-113">Remarks</span></span>  
 <span data-ttu-id="63502-114">Meta verilerin bellek içi kopyası, "içeri aktarma" arabirimlerinden birindeki yöntemler kullanılarak sorgulanabilir veya "yayma" arabirimlerinden birindeki yöntemleri kullanarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="63502-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="63502-115">Hedef dosya CLR meta verileri içermiyorsa, `OpenScope` Yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="63502-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="63502-116">.NET Framework sürüm 1,0 ve sürüm 1,1 ' de bir kapsam, `dwOpenFlags` ofRead olarak ayarlandıysa, paylaşım için uygundur.</span><span class="sxs-lookup"><span data-stu-id="63502-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="63502-117">Diğer bir deyişle, `OpenScope` daha önce açılan bir dosyanın adında sonraki çağrılar varsa, mevcut kapsam yeniden kullanılır ve yeni bir veri yapıları kümesi oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="63502-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="63502-118">Ancak, bu paylaşım nedeniyle sorunlar ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="63502-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="63502-119">.NET Framework sürüm 2,0 ' de, `dwOpenFlags` ofRead olarak ayarlanan ile açılan kapsamlar artık paylaşılmaz.</span><span class="sxs-lookup"><span data-stu-id="63502-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="63502-120">Kapsamın paylaşılmasını sağlamak için ofReadOnly değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="63502-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="63502-121">Bir kapsam paylaşıldığında, "okuma/yazma" meta veri arabirimlerini kullanan sorgular başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="63502-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63502-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63502-122">Requirements</span></span>  
 <span data-ttu-id="63502-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63502-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63502-124">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="63502-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63502-125">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="63502-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63502-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63502-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63502-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63502-127">See also</span></span>

- [<span data-ttu-id="63502-128">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63502-128">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="63502-129">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63502-129">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="63502-130">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63502-130">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="63502-131">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63502-131">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="63502-132">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63502-132">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="63502-133">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63502-133">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="63502-134">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63502-134">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="63502-135">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63502-135">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
