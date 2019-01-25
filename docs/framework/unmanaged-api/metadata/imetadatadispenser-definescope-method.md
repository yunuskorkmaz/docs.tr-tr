---
title: IMetaDataDispenser::DefineScope Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9f9cac2b59f783a81663af0c5eb148367d54e8aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605199"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="4652f-102">IMetaDataDispenser::DefineScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4652f-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="4652f-103">Yeni meta verileri oluşturma bellekte yeni bir alan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4652f-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4652f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4652f-104">Syntax</span></span>  
  
```  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4652f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4652f-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="4652f-106">[in] Oluşturulacak CLSID meta veri yapıları sürümü.</span><span class="sxs-lookup"><span data-stu-id="4652f-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="4652f-107">Bu değer, .NET Framework sürüm 2.0 için CLSID_CorMetaDataRuntime olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4652f-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="4652f-108">[in] Seçeneklerini belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="4652f-108">[in] Flags that specify options.</span></span> <span data-ttu-id="4652f-109">Bu değer, .NET Framework 2.0 için sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4652f-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="4652f-110">[in] Döndürülecek istenen meta veri arayüzü Laboratuvardaki; çağıran, yeni meta verileri oluşturmak için arabirim kullanır.</span><span class="sxs-lookup"><span data-stu-id="4652f-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="4652f-111">Değerini `riid` "Yayımla" arabirimlerinden birini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4652f-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="4652f-112">IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit veya IID_IMetaDataEmit2 değerler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4652f-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="4652f-113">[out] Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4652f-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4652f-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4652f-114">Remarks</span></span>  
 <span data-ttu-id="4652f-115">`DefineScope` bellek içi meta veri tabloları kümesi oluşturur, meta veriler için benzersiz GUID (modülü sürüm tanımlayıcısı veya MVID) oluşturur ve yayılan derleme birimini modülü tablosunda bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4652f-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="4652f-116">Kullanarak bir bütün olarak meta veri kapsama öznitelikler ekleyebilirsiniz [Imetadataemit::setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) veya [Imetadataemit::definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) , uygun şekilde yöntem.</span><span class="sxs-lookup"><span data-stu-id="4652f-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4652f-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4652f-117">Requirements</span></span>  
 <span data-ttu-id="4652f-118">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4652f-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4652f-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4652f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4652f-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="4652f-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4652f-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4652f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4652f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4652f-122">See also</span></span>
- [<span data-ttu-id="4652f-123">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4652f-123">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="4652f-124">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4652f-124">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="4652f-125">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4652f-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="4652f-126">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4652f-126">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4652f-127">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4652f-127">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
