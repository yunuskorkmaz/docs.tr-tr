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
ms.openlocfilehash: 2f9325f3795262a0c33af02f87fc5d3a020658cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177647"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="a141b-102">IMetaDataDispenser::DefineScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a141b-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="a141b-103">Bellekte yeni meta veriler oluşturabileceğiniz yeni bir alan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a141b-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a141b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a141b-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a141b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a141b-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="a141b-106">[içinde] Oluşturulacak meta veri yapılarının sürümünün CLSID'si.</span><span class="sxs-lookup"><span data-stu-id="a141b-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="a141b-107">Bu değer .NET Framework sürüm 2.0 için CLSID_CorMetaDataRuntime olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a141b-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="a141b-108">[içinde] Seçenekleri belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="a141b-108">[in] Flags that specify options.</span></span> <span data-ttu-id="a141b-109">Bu değer .NET Framework 2.0 için sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a141b-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="a141b-110">[içinde] Döndürülecek istenilen meta veri arabiriminin IID'si; arayan yeni meta verileri oluşturmak için arabirimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a141b-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="a141b-111">Değeri "yayılt" arabirimlerinden birini `riid` belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="a141b-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="a141b-112">Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit veya IID_IMetaDataEmit2.</span><span class="sxs-lookup"><span data-stu-id="a141b-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="a141b-113">[çıkış] Döndürülen arabirimin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a141b-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a141b-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a141b-114">Remarks</span></span>  
 <span data-ttu-id="a141b-115">`DefineScope`bellek içi meta veri tabloları kümesi oluşturur, meta veriler için benzersiz bir GUID (modül sürüm tanımlayıcısı veya MVID) oluşturur ve yayılan derleme birimi için modül tablosunda bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a141b-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="a141b-116">[IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) veya [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) yöntemini kullanarak meta veri kapsamına uygun şekilde öznitelikleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a141b-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a141b-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a141b-117">Requirements</span></span>  
 <span data-ttu-id="a141b-118">**Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a141b-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a141b-119">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a141b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a141b-120">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a141b-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a141b-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a141b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a141b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a141b-122">See also</span></span>

- [<span data-ttu-id="a141b-123">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a141b-123">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="a141b-124">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a141b-124">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="a141b-125">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a141b-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="a141b-126">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a141b-126">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a141b-127">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a141b-127">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
