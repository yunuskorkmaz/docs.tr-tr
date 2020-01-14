---
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
ms.openlocfilehash: adbb5eca3b7ffa36d0c963d0dacc3b2afdb664d4
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935557"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="0a1b5-102">LoadTypeLibWithResolver İşlevi</span><span class="sxs-lookup"><span data-stu-id="0a1b5-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="0a1b5-103">Bir tür kitaplığını yükler ve dahili olarak başvurulan tüm tür kitaplıklarını çözümlemek için sağlanan [ıtypeelibresolver arabirimini](itypelibresolver-interface.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-103">Loads a type library and uses the supplied [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a1b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a1b5-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a1b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a1b5-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="0a1b5-106">'ndaki Tür kitaplığının dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="0a1b5-107">'ndaki Tür kitaplığının nasıl kaydedildiğini denetleyen bir [regkind numaralandırma](/windows/win32/api/oleauto/ne-oleauto-regkind) bayrağı.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-107">[in] A [REGKIND enumeration](/windows/win32/api/oleauto/ne-oleauto-regkind) flag that controls how the type library is registered.</span></span> <span data-ttu-id="0a1b5-108">Olası değerleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0a1b5-108">Its possible values are:</span></span>  
  
- <span data-ttu-id="0a1b5-109">`REGKIND_DEFAULT`: varsayılan kayıt davranışını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
- <span data-ttu-id="0a1b5-110">`REGKIND_REGISTER`: Bu tür kitaplığını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
- <span data-ttu-id="0a1b5-111">`REGKIND_NONE`: Bu tür kitaplığını kaydetme.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="0a1b5-112">'ndaki [Itypeelibresolver arabiriminin](itypelibresolver-interface.md)uygulanması için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="0a1b5-113">dışı Yüklenmekte olan tür kitaplığına bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a1b5-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0a1b5-114">Return Value</span></span>  
 <span data-ttu-id="0a1b5-115">Aşağıdaki tabloda listelenen HRESULT değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="0a1b5-116">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="0a1b5-116">Return value</span></span>|<span data-ttu-id="0a1b5-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a1b5-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="0a1b5-118">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="0a1b5-119">Bellek yetersiz.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="0a1b5-120">İşaretçilerin bir veya daha fazlası geçersiz.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="0a1b5-121">Bağımsız değişkenlerden biri veya birkaçı geçersiz.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="0a1b5-122">İşlev dosyaya yazamadı.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="0a1b5-123">Sistem kayıt veritabanı açılamadı.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="0a1b5-124">Tür kitaplığı açılamadı.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="0a1b5-125">Tür kitaplığı veya DLL yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a1b5-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a1b5-126">Remarks</span></span>  
 <span data-ttu-id="0a1b5-127">[Tlbexp. exe (tür kitaplığı verme programı)](../../tools/tlbexp-exe-type-library-exporter.md) , derlemeden tür kitaplığı dönüştürme işlemi sırasında `LoadTypeLibWithResolver` işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-127">The [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="0a1b5-128">Bu işlev, kayıt defterine en az erişimli olan belirtilen tür kitaplığını yükler.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="0a1b5-129">Bu işlev daha sonra, her birinin yüklenmesi ve üst tür kitaplığına eklenmesi gereken dahili olarak Başvurulmuş tür kitaplıkları için tür kitaplığını inceler.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="0a1b5-130">Başvurulan bir tür kitaplığının yüklenebilmesi için, başvuru dosyası yolunun tam dosya yoluna çözülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="0a1b5-131">Bu, `pTlbResolver` parametresine geçirilen [ıtypeelibresolver arabirimi](itypelibresolver-interface.md)tarafından verilen [resolvettypeınfo yöntemi](resolvetypelib-method.md) aracılığıyla gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-131">This is accomplished through the [ResolveTypeLib method](resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="0a1b5-132">Başvurulan tür kitaplığının tam dosya yolu bilindiğinde `LoadTypeLibWithResolver` işlevi yüklenir ve başvurulan tür kitaplığını üst tür kitaplığına ekler ve birleştirilmiş bir ana tür kitaplığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="0a1b5-133">İşlev, iç başvurulan tüm tür kitaplıklarını çözümleyip yükledikten sonra, `pptlib` parametresinde ana çözümlenen tür kitaplığına bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="0a1b5-134">`LoadTypeLibWithResolver` işlevi genellikle [Tlbexp. exe (tür kitaplığı verme programı)](../../tools/tlbexp-exe-type-library-exporter.md)tarafından çağrılır ve bu, `pTlbResolver` parametresinde kendi Iç [ITypeLibResolver arabirimi](itypelibresolver-interface.md) uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="0a1b5-135">`LoadTypeLibWithResolver` doğrudan çağırırsanız, kendi [ITypeLibResolver arabirimi](itypelibresolver-interface.md) uygulamanızı sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a1b5-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a1b5-136">Requirements</span></span>  
 <span data-ttu-id="0a1b5-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a1b5-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a1b5-138">**Üst bilgi:** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="0a1b5-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="0a1b5-139">**Kitaplık:** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="0a1b5-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="0a1b5-140">**.NET Framework sürümü:** 3,5, 3,0, 2,0</span><span class="sxs-lookup"><span data-stu-id="0a1b5-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a1b5-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a1b5-141">See also</span></span>

- [<span data-ttu-id="0a1b5-142">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0a1b5-142">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="0a1b5-143">LoadTypeLibEx Işlevi</span><span class="sxs-lookup"><span data-stu-id="0a1b5-143">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
