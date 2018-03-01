---
title: "LoadTypeLibWithResolver İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f069d09f25575c39db097024384ad1bf14eaaf02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="d032e-102">LoadTypeLibWithResolver İşlevi</span><span class="sxs-lookup"><span data-stu-id="d032e-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="d032e-103">Tür kitaplığını yükler ve sağlanan kullanır [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) herhangi dahili olarak başvurulan tür kitaplıklarının çözümlemek için.</span><span class="sxs-lookup"><span data-stu-id="d032e-103">Loads a type library and uses the supplied [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d032e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d032e-104">Syntax</span></span>  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d032e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d032e-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="d032e-106">[in] Tür kitaplığı dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="d032e-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="d032e-107">[in] A [REGKIND numaralandırma](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx) tür kitaplığının nasıl kayıtlı denetimleri bayrağı.</span><span class="sxs-lookup"><span data-stu-id="d032e-107">[in] A [REGKIND enumeration](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx) flag that controls how the type library is registered.</span></span> <span data-ttu-id="d032e-108">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d032e-108">Its possible values are:</span></span>  
  
-   <span data-ttu-id="d032e-109">`REGKIND_DEFAULT`: Varsayılan kayıt davranışı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d032e-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
-   <span data-ttu-id="d032e-110">`REGKIND_REGISTER`: Bu tür kitaplığının kaydı.</span><span class="sxs-lookup"><span data-stu-id="d032e-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
-   <span data-ttu-id="d032e-111">`REGKIND_NONE`: Bu tür kitaplığı kaydı.</span><span class="sxs-lookup"><span data-stu-id="d032e-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="d032e-112">[in] Uygulaması için bir işaretçi [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d032e-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="d032e-113">[out] Yüklenmekte türü kitaplığına bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="d032e-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d032e-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d032e-114">Return Value</span></span>  
 <span data-ttu-id="d032e-115">Aşağıdaki tabloda listelenen HRESULT değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="d032e-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="d032e-116">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d032e-116">Return value</span></span>|<span data-ttu-id="d032e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d032e-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="d032e-118">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="d032e-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="d032e-119">Bellek yetersiz.</span><span class="sxs-lookup"><span data-stu-id="d032e-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="d032e-120">Bir veya daha fazla işaretçileri geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="d032e-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="d032e-121">Bir veya daha fazla bağımsız değişken geçersiz.</span><span class="sxs-lookup"><span data-stu-id="d032e-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="d032e-122">İşlev dosyasına yazılamadı.</span><span class="sxs-lookup"><span data-stu-id="d032e-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="d032e-123">Sistem kayıt veritabanı açılamadı.</span><span class="sxs-lookup"><span data-stu-id="d032e-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="d032e-124">Tür kitaplığı açılamadı.</span><span class="sxs-lookup"><span data-stu-id="d032e-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="d032e-125">Tür kitaplığı veya DLL yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="d032e-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d032e-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d032e-126">Remarks</span></span>  
 <span data-ttu-id="d032e-127">[Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) çağrıları `LoadTypeLibWithResolver` derleme için tür kitaplığı dönüştürme işlemi sırasında işlevi.</span><span class="sxs-lookup"><span data-stu-id="d032e-127">The [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="d032e-128">Bu işlev kayıt defterine en az düzeyde erişim ile belirtilen tür kitaplığı yükler.</span><span class="sxs-lookup"><span data-stu-id="d032e-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="d032e-129">İşlev sonra her biri gerekir yüklenmesi ve üst tür kitaplığı'na eklenen dahili olarak başvurulan tür kitaplıkları için tür kitaplığı inceler.</span><span class="sxs-lookup"><span data-stu-id="d032e-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="d032e-130">Başvurulan tür kitaplığını yüklenmeden önce başvuru dosya yoluna bir tam dosya yolunu çözümlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="d032e-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="d032e-131">Bu aracılığıyla gerçekleştirilir [ResolveTypeLib yöntemi](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) tarafından sağlanan [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), içinde geçirilen `pTlbResolver` parametresi.</span><span class="sxs-lookup"><span data-stu-id="d032e-131">This is accomplished through the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="d032e-132">Başvurulan tür kitaplığı tam dosya yolunu bilindiğinde `LoadTypeLibWithResolver` işlevi yükler ve başvurulan tür kitaplığı birleşik ana tür kitaplığı oluşturma üst tür kitaplığına ekler.</span><span class="sxs-lookup"><span data-stu-id="d032e-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="d032e-133">İşlev çözümler ve tüm dahili olarak başvurulan tür kitaplıklarını yükler sonra ana çözümlenmiş Tür Kitaplığı'nda bir başvuru döndürür `pptlib` parametresi.</span><span class="sxs-lookup"><span data-stu-id="d032e-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="d032e-134">`LoadTypeLibWithResolver` İşlev çağrılan genellikle [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), kendi iç sağladığı [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) uygulamasında `pTlbResolver` parametre.</span><span class="sxs-lookup"><span data-stu-id="d032e-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="d032e-135">Çağırırsanız `LoadTypeLibWithResolver` doğrudan kendi sağlamanız gerekir [Itypelibresolver arabirimi](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) uygulaması.</span><span class="sxs-lookup"><span data-stu-id="d032e-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d032e-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d032e-136">Requirements</span></span>  
 <span data-ttu-id="d032e-137">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d032e-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d032e-138">**Başlık:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="d032e-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="d032e-139">**Kitaplığı:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="d032e-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="d032e-140">**.NET framework sürümü:** 3.5, 3.0, 2.0</span><span class="sxs-lookup"><span data-stu-id="d032e-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d032e-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d032e-141">See Also</span></span>  
 [<span data-ttu-id="d032e-142">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d032e-142">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="d032e-143">[LoadTypeLibEx işlevi](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="d032e-143">[LoadTypeLibEx Function](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)</span></span>
