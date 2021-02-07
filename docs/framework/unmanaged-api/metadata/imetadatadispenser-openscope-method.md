---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatadağıtıcı:: OpenScope Yöntemi'
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
ms.openlocfilehash: a1fa9a955bfc38ee4b2f23efbe8e492877a3d0c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753625"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="5fc67-103">IMetaDataDispenser::OpenScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5fc67-103">IMetaDataDispenser::OpenScope Method</span></span>

<span data-ttu-id="5fc67-104">Mevcut, disk üzerindeki bir dosyayı açar ve meta verilerini belleğe eşler.</span><span class="sxs-lookup"><span data-stu-id="5fc67-104">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fc67-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fc67-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fc67-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5fc67-106">Parameters</span></span>  

 `szScope`  
 <span data-ttu-id="5fc67-107">'ndaki Açılacak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="5fc67-107">[in] The name of the file to be opened.</span></span> <span data-ttu-id="5fc67-108">Dosya, ortak dil çalışma zamanı (CLR) meta verilerini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="5fc67-108">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="5fc67-109">'ndaki Açma için modu (okuma, yazma, vb.) belirtmek için [CorOpenFlags](coropenflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="5fc67-109">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="5fc67-110">'ndaki Döndürülecek istenen meta veri arabiriminin IID 'si; çağıran, meta verileri içeri aktarmak (okumak) veya yayma (yazmak) için arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5fc67-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="5fc67-111">Değeri, `riid` "import" veya "yayma" arabirimlerinden birini belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="5fc67-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="5fc67-112">Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="5fc67-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="5fc67-113">dışı Döndürülen arabirime yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5fc67-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fc67-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5fc67-114">Remarks</span></span>  

 <span data-ttu-id="5fc67-115">Meta verilerin bellek içi kopyası, "içeri aktarma" arabirimlerinden birindeki yöntemler kullanılarak sorgulanabilir veya "yayma" arabirimlerinden birindeki yöntemleri kullanarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="5fc67-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="5fc67-116">Hedef dosya CLR meta verileri içermiyorsa, `OpenScope` Yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5fc67-116">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="5fc67-117">.NET Framework sürüm 1,0 ve sürüm 1,1 ' de bir kapsam, `dwOpenFlags` ofRead olarak ayarlandıysa, paylaşım için uygundur.</span><span class="sxs-lookup"><span data-stu-id="5fc67-117">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="5fc67-118">Diğer bir deyişle, `OpenScope` daha önce açılan bir dosyanın adında sonraki çağrılar varsa, mevcut kapsam yeniden kullanılır ve yeni bir veri yapıları kümesi oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="5fc67-118">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="5fc67-119">Ancak, bu paylaşım nedeniyle sorunlar ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="5fc67-119">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="5fc67-120">.NET Framework sürüm 2,0 ' de, `dwOpenFlags` ofRead olarak ayarlanan ile açılan kapsamlar artık paylaşılmaz.</span><span class="sxs-lookup"><span data-stu-id="5fc67-120">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="5fc67-121">Kapsamın paylaşılmasını sağlamak için ofReadOnly değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5fc67-121">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="5fc67-122">Bir kapsam paylaşıldığında, "okuma/yazma" meta veri arabirimlerini kullanan sorgular başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5fc67-122">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fc67-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5fc67-123">Requirements</span></span>  

 <span data-ttu-id="5fc67-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fc67-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fc67-125">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5fc67-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5fc67-126">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5fc67-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5fc67-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fc67-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fc67-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fc67-128">See also</span></span>

- [<span data-ttu-id="5fc67-129">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5fc67-129">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="5fc67-130">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5fc67-130">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="5fc67-131">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5fc67-131">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="5fc67-132">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5fc67-132">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="5fc67-133">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5fc67-133">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="5fc67-134">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5fc67-134">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="5fc67-135">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5fc67-135">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5fc67-136">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5fc67-136">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
