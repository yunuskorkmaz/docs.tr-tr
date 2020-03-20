---
title: IMetaDataAssemblyImport::FindAssembliesByName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
ms.openlocfilehash: c0f81e3767d4ea3bc336203fbe8c914b4e2bd07b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177794"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="1e65c-102">IMetaDataAssemblyImport::FindAssembliesByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e65c-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="1e65c-103">Başvuruları çözmek için ortak dil `szAssemblyName` çalışma zamanı (CLR) tarafından kullanılan standart kuralları kullanarak, belirtilen parametreye sahip bir dizi derleme alır.</span><span class="sxs-lookup"><span data-stu-id="1e65c-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e65c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e65c-104">Syntax</span></span>  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,
    [in]  LPCWSTR     szPrivateBin,
    [in]  LPCWSTR     szAssemblyName,
    [out] IUnknown    *ppIUnk[],
    [in]  ULONG       cMax,
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e65c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e65c-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="1e65c-106">[içinde] Verilen derlemeiçin aramak için kök dizin.</span><span class="sxs-lookup"><span data-stu-id="1e65c-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="1e65c-107">Bu değer , `null`yalnızca `FindAssembliesByName` derleme için genel montaj önbelleğinde görünecek şekilde ayarlanırsa.</span><span class="sxs-lookup"><span data-stu-id="1e65c-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="1e65c-108">[içinde] Alt dizinin altında, derlemenin arandığı yarı sütunlu sınırlı alt dizinlerin (örneğin, "bin2") listesi.</span><span class="sxs-lookup"><span data-stu-id="1e65c-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="1e65c-109">Bu dizinler, varsayılan sondalama kurallarında belirtilenlere ek olarak incelenir.</span><span class="sxs-lookup"><span data-stu-id="1e65c-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="1e65c-110">[içinde] Bulmak için derleme adı.</span><span class="sxs-lookup"><span data-stu-id="1e65c-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="1e65c-111">Bu dize biçimi için <xref:System.Reflection.AssemblyName>sınıf başvuru sayfasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1e65c-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="1e65c-112">[içinde] Arabirim işaretçileri koymak için [tip IUnknown](/cpp/atl/iunknown) bir dizi. `IMetadataAssemblyImport`</span><span class="sxs-lookup"><span data-stu-id="1e65c-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1e65c-113">[çıkış] Yerleştirilebilen en fazla arayüz işaretçisi `ppIUnk`sayısı.</span><span class="sxs-lookup"><span data-stu-id="1e65c-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="1e65c-114">[çıkış] Döndürülen arabirim işaretçilerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="1e65c-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="1e65c-115">Diğer bir deyişle, aslında yerleştirilen arabirim işaretçilerinin `ppIUnk`sayısı.</span><span class="sxs-lookup"><span data-stu-id="1e65c-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e65c-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1e65c-116">Return Value</span></span>  
  
|<span data-ttu-id="1e65c-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1e65c-117">HRESULT</span></span>|<span data-ttu-id="1e65c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e65c-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1e65c-119">`FindAssembliesByName`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1e65c-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1e65c-120">Meclis falan yok.</span><span class="sxs-lookup"><span data-stu-id="1e65c-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e65c-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e65c-121">Remarks</span></span>  
 <span data-ttu-id="1e65c-122">Bir derleme adı `FindAssembliesByName` verildiğinde, yöntem derleme başvurularını çözmek için standart kuralları izleyerek derlemeyi bulur.</span><span class="sxs-lookup"><span data-stu-id="1e65c-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="1e65c-123">(Daha fazla bilgi [için, Çalışma Zamanı Derlemeleri Nasıl Bulur'a](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)bakın.) `FindAssembliesByName` arayanın, uygulama tabanı ve özel arama yolu gibi derleme çözümleyici bağlamının çeşitli yönlerini yapılandırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1e65c-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="1e65c-124">Yöntem, `FindAssembliesByName` derleme çözümleme mantığını çağırmak için CLR'nin işlemde başlatılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1e65c-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="1e65c-125">Bu nedenle, aramadan `FindAssembliesByName`önce [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (COINITEE_DEFAULT geçen) aramanız ve ardından [CoUninitializeCor'a](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)bir çağrı ile izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e65c-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="1e65c-126">`FindAssembliesByName`Geçirilen derleme adının montaj bildirimini içeren dosyaya bir [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) işaretçisi verir.</span><span class="sxs-lookup"><span data-stu-id="1e65c-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="1e65c-127">Verilen derleme adı tam olarak belirtilmemişse (örneğin, bir sürüm içermiyorsa), birden çok derleme döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="1e65c-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="1e65c-128">`FindAssembliesByName`genellikle derleme zamanında başvurulan bir derleme bulmaya çalışan bir derleyici tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1e65c-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e65c-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e65c-129">Requirements</span></span>  
 <span data-ttu-id="1e65c-130">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e65c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e65c-131">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1e65c-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1e65c-132">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1e65c-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1e65c-133">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e65c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e65c-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e65c-134">See also</span></span>

- [<span data-ttu-id="1e65c-135">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="1e65c-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="1e65c-136">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e65c-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
