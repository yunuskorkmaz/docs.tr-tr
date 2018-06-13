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
ms.openlocfilehash: 11382f00839917185ba3c85b8fbae5c32d0b0d4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448616"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="86d28-102">IMetaDataDispenser::DefineScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86d28-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="86d28-103">Yeni bir alan yeni meta oluşturabileceğiniz bellekte oluşturur.</span><span class="sxs-lookup"><span data-stu-id="86d28-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86d28-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86d28-104">Syntax</span></span>  
  
```  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86d28-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86d28-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="86d28-106">[in] Oluşturulacak CLSID meta veri yapılarını sürümünün.</span><span class="sxs-lookup"><span data-stu-id="86d28-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="86d28-107">Bu değer .NET Framework sürüm 2.0 için CLSID_CorMetaDataRuntime olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86d28-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="86d28-108">[in] Seçeneklerini belirtin bayraklar.</span><span class="sxs-lookup"><span data-stu-id="86d28-108">[in] Flags that specify options.</span></span> <span data-ttu-id="86d28-109">Bu değer, .NET Framework 2.0 için sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86d28-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="86d28-110">[in] Döndürülecek istenen meta veri arabirimi IID; çağıran ve yeni meta oluşturmak için arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="86d28-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="86d28-111">Değeri `riid` "Yayımla" arabirimleri birini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="86d28-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="86d28-112">Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit veya IID_IMetaDataEmit2 değerleridir.</span><span class="sxs-lookup"><span data-stu-id="86d28-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="86d28-113">[out] Döndürülen arabirimi yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="86d28-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86d28-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86d28-114">Remarks</span></span>  
 <span data-ttu-id="86d28-115">`DefineScope` bellek içi meta veri tabloları kümesi oluşturur, meta veriler için benzersiz GUID (Modül sürümü tanıtıcısı veya MVID) oluşturur ve gösterilmesini derleme birimini modülü tablosunda bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="86d28-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="86d28-116">Kullanarak bir bütün olarak meta veri kapsama öznitelikler ekleyebilirsiniz [Imetadataemit::setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) veya [Imetadataemit::definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) uygun şekilde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="86d28-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86d28-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86d28-117">Requirements</span></span>  
 <span data-ttu-id="86d28-118">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86d28-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86d28-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="86d28-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86d28-120">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="86d28-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86d28-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86d28-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d28-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86d28-122">See Also</span></span>  
 [<span data-ttu-id="86d28-123">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86d28-123">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="86d28-124">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86d28-124">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="86d28-125">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86d28-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="86d28-126">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86d28-126">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="86d28-127">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86d28-127">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
