---
description: ': Imetadatadağıtıcı::D efineScope yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: b7a7870ec06af4c08a4ef3609077eb93f74da776
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789248"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="9039a-103">IMetaDataDispenser::DefineScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9039a-103">IMetaDataDispenser::DefineScope Method</span></span>

<span data-ttu-id="9039a-104">Bellekte yeni meta veri oluşturabileceğiniz yeni bir alan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9039a-104">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9039a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9039a-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9039a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9039a-106">Parameters</span></span>  

 `rclsid`  
 <span data-ttu-id="9039a-107">'ndaki Oluşturulacak meta veri yapıları sürümünün CLSID değeri.</span><span class="sxs-lookup"><span data-stu-id="9039a-107">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="9039a-108">Bu değer, .NET Framework sürüm 2,0 için CLSID_CorMetaDataRuntime olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9039a-108">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="9039a-109">'ndaki Seçenekleri belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="9039a-109">[in] Flags that specify options.</span></span> <span data-ttu-id="9039a-110">Bu değer, .NET Framework 2,0 için sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9039a-110">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="9039a-111">'ndaki Döndürülecek istenen meta veri arabiriminin IID 'si; çağıran, yeni meta verileri oluşturmak için arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9039a-111">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="9039a-112">Değerinin `riid` "yayma" arabirimlerinden birini belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9039a-112">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="9039a-113">Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit veya IID_IMetaDataEmit2.</span><span class="sxs-lookup"><span data-stu-id="9039a-113">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="9039a-114">dışı Döndürülen arabirime yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9039a-114">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9039a-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9039a-115">Remarks</span></span>  

 <span data-ttu-id="9039a-116">`DefineScope` bellek içi meta veri tabloları kümesi oluşturur, meta veriler için benzersiz bir GUID (Modül sürümü tanımlayıcısı veya MVıD) oluşturur ve yayılmakta olan derleme biriminin modül tablosunda bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9039a-116">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="9039a-117">[Imetadatayayma:: SetModuleProps](imetadataemit-setmoduleprops-method.md) veya [ımetadatayayma::D efineCustomAttribute](imetadataemit-definecustomattribute-method.md) metodunu uygun şekilde kullanarak bir bütün olarak meta veri kapsamına öznitelikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9039a-117">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9039a-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9039a-118">Requirements</span></span>  

 <span data-ttu-id="9039a-119">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9039a-119">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9039a-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9039a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9039a-121">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="9039a-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9039a-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9039a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9039a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9039a-123">See also</span></span>

- [<span data-ttu-id="9039a-124">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9039a-124">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="9039a-125">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9039a-125">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="9039a-126">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9039a-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="9039a-127">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9039a-127">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9039a-128">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9039a-128">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
