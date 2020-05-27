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
ms.openlocfilehash: 05902436c09d082f90af01f48c7e918650317ce7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009424"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="1da0a-102">IMetaDataAssemblyImport::FindAssembliesByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1da0a-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="1da0a-103">`szAssemblyName`Başvuruları çözümlemek için ortak dil çalışma zamanı (CLR) tarafından kullanılan standart kuralları kullanarak belirtilen parametreye sahip derlemelerin dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="1da0a-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1da0a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1da0a-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1da0a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1da0a-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="1da0a-106">'ndaki Verilen derlemenin aranacağı kök dizin.</span><span class="sxs-lookup"><span data-stu-id="1da0a-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="1da0a-107">Bu değer olarak ayarlandıysa `null` , `FindAssembliesByName` yalnızca derleme için genel derleme önbelleğinde görünür.</span><span class="sxs-lookup"><span data-stu-id="1da0a-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="1da0a-108">'ndaki Derlemenin aranacağı kök dizin altında, noktalı virgülle ayrılmış alt dizinlerin (örneğin, "bin; bin2") bir listesi.</span><span class="sxs-lookup"><span data-stu-id="1da0a-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="1da0a-109">Bu dizinler, varsayılan yoklama kurallarında belirtienlere ek olarak araştırlanır.</span><span class="sxs-lookup"><span data-stu-id="1da0a-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="1da0a-110">'ndaki Bulunacak derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="1da0a-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="1da0a-111">Bu dizenin biçimi için sınıf başvurusu sayfasında tanımlanmıştır <xref:System.Reflection.AssemblyName> .</span><span class="sxs-lookup"><span data-stu-id="1da0a-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="1da0a-112">'ndaki Arabirim işaretçilerine yerleştirilecek [IUnknown](/cpp/atl/iunknown) türünde bir dizi `IMetadataAssemblyImport` .</span><span class="sxs-lookup"><span data-stu-id="1da0a-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1da0a-113">dışı İçine yerleştirilebilecek en fazla arabirim işaretçisi sayısı `ppIUnk` .</span><span class="sxs-lookup"><span data-stu-id="1da0a-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="1da0a-114">dışı Döndürülen arabirim işaretçilerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="1da0a-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="1da0a-115">Diğer bir deyişle, gerçekte içine yerleştirilmiş olan arabirim işaretçilerinin sayısı `ppIUnk` .</span><span class="sxs-lookup"><span data-stu-id="1da0a-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1da0a-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1da0a-116">Return Value</span></span>  
  
|<span data-ttu-id="1da0a-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1da0a-117">HRESULT</span></span>|<span data-ttu-id="1da0a-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1da0a-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1da0a-119">`FindAssembliesByName`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1da0a-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1da0a-120">Hiçbir derleme yok.</span><span class="sxs-lookup"><span data-stu-id="1da0a-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1da0a-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1da0a-121">Remarks</span></span>  
 <span data-ttu-id="1da0a-122">Derleme adı verildiğinde, yöntem derleme `FindAssembliesByName` başvurularını çözümlemek için standart kuralları izleyerek derlemeyi bulur.</span><span class="sxs-lookup"><span data-stu-id="1da0a-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="1da0a-123">(Daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName`çağıranın, uygulama temeli ve özel arama yolu gibi bütünleştirilmiş kod çözümleyici bağlamının çeşitli yönlerini yapılandırmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="1da0a-123">(For more information, see [How the Runtime Locates Assemblies](../../deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="1da0a-124">`FindAssembliesByName`Yöntemi, derleme çözümleme mantığını çağırmak IÇIN clr 'nin işlemde başlatılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1da0a-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="1da0a-125">Bu nedenle, çağrılmadan önce [Coınitialeee](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (geçirme COINITEE_DEFAULT) yöntemini çağırmanız `FindAssembliesByName` ve sonra [Counınitializecor](../hosting/couninitializecor-function.md)çağrısı ile izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1da0a-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="1da0a-126">`FindAssembliesByName`geçirilen derleme adı için derleme bildirimini içeren dosyaya bir [IMetaDataImport](imetadataimport-interface.md) işaretçisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="1da0a-126">`FindAssembliesByName` returns an [IMetaDataImport](imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="1da0a-127">Verilen derleme adı tam olarak belirtilmemişse (örneğin, bir sürüm içermiyorsa), birden çok derleme döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="1da0a-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="1da0a-128">`FindAssembliesByName`, derleme zamanında başvurulan bir derlemeyi bulmayı deneyen bir derleyici tarafından yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1da0a-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1da0a-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1da0a-129">Requirements</span></span>  
 <span data-ttu-id="1da0a-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1da0a-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1da0a-131">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1da0a-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1da0a-132">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1da0a-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1da0a-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1da0a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1da0a-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1da0a-134">See also</span></span>

- [<span data-ttu-id="1da0a-135">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="1da0a-135">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="1da0a-136">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1da0a-136">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
