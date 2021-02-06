---
description: ': LoadTypeLibWithResolver Işlevi hakkında daha fazla bilgi'
title: LoadTypeLibWithResolver İşlevi
ms.date: 03/30/2017
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
ms.openlocfilehash: 6747199364a549d922ad73bfac3e93b329d1172a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646224"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="0e24d-103">LoadTypeLibWithResolver İşlevi</span><span class="sxs-lookup"><span data-stu-id="0e24d-103">LoadTypeLibWithResolver Function</span></span>

<span data-ttu-id="0e24d-104">Bir tür kitaplığını yükler ve dahili olarak başvurulan tüm tür kitaplıklarını çözümlemek için sağlanan [ıtypeelibresolver arabirimini](itypelibresolver-interface.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="0e24d-104">Loads a type library and uses the supplied [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e24d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e24d-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e24d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e24d-106">Parameters</span></span>  

 `szFile`  
 <span data-ttu-id="0e24d-107">'ndaki Tür kitaplığının dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="0e24d-107">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="0e24d-108">'ndaki Tür kitaplığının nasıl kaydedildiğini denetleyen bir [regkind numaralandırma](/windows/win32/api/oleauto/ne-oleauto-regkind) bayrağı.</span><span class="sxs-lookup"><span data-stu-id="0e24d-108">[in] A [REGKIND enumeration](/windows/win32/api/oleauto/ne-oleauto-regkind) flag that controls how the type library is registered.</span></span> <span data-ttu-id="0e24d-109">Olası değerleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0e24d-109">Its possible values are:</span></span>  
  
- <span data-ttu-id="0e24d-110">`REGKIND_DEFAULT`: Varsayılan kayıt davranışını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e24d-110">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
- <span data-ttu-id="0e24d-111">`REGKIND_REGISTER`: Bu tür kitaplığını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="0e24d-111">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
- <span data-ttu-id="0e24d-112">`REGKIND_NONE`: Bu tür kitaplığını kaydetme.</span><span class="sxs-lookup"><span data-stu-id="0e24d-112">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="0e24d-113">'ndaki [Itypeelibresolver arabiriminin](itypelibresolver-interface.md)uygulanması için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0e24d-113">[in] A pointer to the implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="0e24d-114">dışı Yüklenmekte olan tür kitaplığına bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="0e24d-114">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e24d-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0e24d-115">Return Value</span></span>  

 <span data-ttu-id="0e24d-116">Aşağıdaki tabloda listelenen HRESULT değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="0e24d-116">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="0e24d-117">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="0e24d-117">Return value</span></span>|<span data-ttu-id="0e24d-118">Anlamı</span><span class="sxs-lookup"><span data-stu-id="0e24d-118">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="0e24d-119">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="0e24d-119">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="0e24d-120">Bellek yetersiz.</span><span class="sxs-lookup"><span data-stu-id="0e24d-120">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="0e24d-121">İşaretçilerin bir veya daha fazlası geçersiz.</span><span class="sxs-lookup"><span data-stu-id="0e24d-121">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="0e24d-122">Bağımsız değişkenlerden biri veya birkaçı geçersiz.</span><span class="sxs-lookup"><span data-stu-id="0e24d-122">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="0e24d-123">İşlev dosyaya yazamadı.</span><span class="sxs-lookup"><span data-stu-id="0e24d-123">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="0e24d-124">Sistem kayıt veritabanı açılamadı.</span><span class="sxs-lookup"><span data-stu-id="0e24d-124">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="0e24d-125">Tür kitaplığı açılamadı.</span><span class="sxs-lookup"><span data-stu-id="0e24d-125">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="0e24d-126">Tür kitaplığı veya DLL yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="0e24d-126">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e24d-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e24d-127">Remarks</span></span>  

 <span data-ttu-id="0e24d-128">[Tlbexp.exe (tür kitaplığı verme programı)](../../tools/tlbexp-exe-type-library-exporter.md) , `LoadTypeLibWithResolver` derlemeyi tür kitaplığı dönüştürme işlemi sırasında işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="0e24d-128">The [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="0e24d-129">Bu işlev, kayıt defterine en az erişimli olan belirtilen tür kitaplığını yükler.</span><span class="sxs-lookup"><span data-stu-id="0e24d-129">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="0e24d-130">Bu işlev daha sonra, her birinin yüklenmesi ve üst tür kitaplığına eklenmesi gereken dahili olarak Başvurulmuş tür kitaplıkları için tür kitaplığını inceler.</span><span class="sxs-lookup"><span data-stu-id="0e24d-130">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="0e24d-131">Başvurulan bir tür kitaplığının yüklenebilmesi için, başvuru dosyası yolunun tam dosya yoluna çözülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e24d-131">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="0e24d-132">Bu, parametreye geçilen [ITypeLibResolver arabirimi](itypelibresolver-interface.md)tarafından verilen [resolvettypeınfo yöntemi](resolvetypelib-method.md) aracılığıyla gerçekleştirilir `pTlbResolver` .</span><span class="sxs-lookup"><span data-stu-id="0e24d-132">This is accomplished through the [ResolveTypeLib method](resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="0e24d-133">Başvurulan tür kitaplığının tam dosya yolu bilindiğinde, `LoadTypeLibWithResolver` işlev yüklenir ve başvurulan tür kitaplığını üst tür kitaplığına ekler ve birleştirilmiş bir ana tür kitaplığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e24d-133">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="0e24d-134">İşlev, iç başvurulan tüm tür kitaplıklarını çözümleyip yükledikten sonra, parametresindeki ana çözümlenen tür kitaplığına bir başvuru döndürür `pptlib` .</span><span class="sxs-lookup"><span data-stu-id="0e24d-134">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="0e24d-135">`LoadTypeLibWithResolver`İşlev genellikle parametresinde kendi Iç [ITypeLibResolver arabirimi](itypelibresolver-interface.md) uygulamasını sağlayan [Tlbexp.exe (tür kitaplığı verme programı)](../../tools/tlbexp-exe-type-library-exporter.md)tarafından çağrılır `pTlbResolver` .</span><span class="sxs-lookup"><span data-stu-id="0e24d-135">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="0e24d-136">Doğrudan çağrı yaparsanız `LoadTypeLibWithResolver` kendi [ITypeLibResolver arabirimi](itypelibresolver-interface.md) uygulamanızı sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e24d-136">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e24d-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e24d-137">Requirements</span></span>  

 <span data-ttu-id="0e24d-138">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e24d-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e24d-139">**Üst bilgi:** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="0e24d-139">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="0e24d-140">**Kitaplık:** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="0e24d-140">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="0e24d-141">**.NET Framework sürümü:** 3,5, 3,0, 2,0</span><span class="sxs-lookup"><span data-stu-id="0e24d-141">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e24d-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e24d-142">See also</span></span>

- [<span data-ttu-id="0e24d-143">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0e24d-143">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="0e24d-144">LoadTypeLibEx Işlevi</span><span class="sxs-lookup"><span data-stu-id="0e24d-144">LoadTypeLibEx Function</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
