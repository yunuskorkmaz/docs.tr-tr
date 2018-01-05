---
title: "IMetaDataAssemblyImport::FindAssembliesByName Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindAssembliesByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d6518fdcf1bef8eaea74818f69f46bb6df26e31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="37856-102">IMetaDataAssemblyImport::FindAssembliesByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37856-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="37856-103">Belirtilen derleme dizisi alır `szAssemblyName` başvurularını çözümlemek için ortak dil çalışma zamanı (CLR) tarafından kullanılan standart kurallar kullanarak parametresi.</span><span class="sxs-lookup"><span data-stu-id="37856-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37856-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37856-104">Syntax</span></span>  
  
```  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37856-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="37856-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="37856-106">[in] Verilen derleme için aranacak kök dizininde.</span><span class="sxs-lookup"><span data-stu-id="37856-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="37856-107">Bu değer ayarlanırsa `null`, `FindAssembliesByName` yalnızca genel derleme önbelleğinde derleme için arar.</span><span class="sxs-lookup"><span data-stu-id="37856-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="37856-108">[in] Noktalı virgülle ayrılmış alt dizinleri (örneğin, "depo; Kutu2"), derleme için aranacağı kök dizininin altında bir listesi.</span><span class="sxs-lookup"><span data-stu-id="37856-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="37856-109">Algılama kuralları varsayılan olarak belirtilen yanı sıra bu dizinleri sıklığının.</span><span class="sxs-lookup"><span data-stu-id="37856-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="37856-110">[in] Bulunacak derleme adı.</span><span class="sxs-lookup"><span data-stu-id="37856-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="37856-111">Bu dize biçimi sınıfı başvuru sayfası için tanımlanan <xref:System.Reflection.AssemblyName>.</span><span class="sxs-lookup"><span data-stu-id="37856-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="37856-112">[in] Türünde bir dizi <<!--zzxref:IUnknown --> `IUnknown`> yerleştirileceği `IMetadataAssemblyImport` arabirim işaretçileri.</span><span class="sxs-lookup"><span data-stu-id="37856-112">[in] An array of type <<!--zzxref:IUnknown --> `IUnknown`> in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="37856-113">[out] Yerleştirilebilir arabirim işaretçileri en fazla `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="37856-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="37856-114">[out] Döndürülen arabirim işaretçileri sayısı.</span><span class="sxs-lookup"><span data-stu-id="37856-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="37856-115">Diğer bir deyişle, arabirim işaretçileri sayısı gerçekte yerleştirilen `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="37856-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37856-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="37856-116">Return Value</span></span>  
  
|<span data-ttu-id="37856-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37856-117">HRESULT</span></span>|<span data-ttu-id="37856-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37856-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="37856-119">`FindAssembliesByName`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="37856-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="37856-120">Hiçbir derlemeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="37856-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37856-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37856-121">Remarks</span></span>  
 <span data-ttu-id="37856-122">Bir derleme adı verilen `FindAssembliesByName` yöntemi derleme başvurularını çözmek için standart kurallar izleyerek derlemeyi bulur.</span><span class="sxs-lookup"><span data-stu-id="37856-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="37856-123">(Daha fazla bilgi için bkz: [nasıl çalışma zamanı bulur derlemeleri](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` arayanın derleme Çözümleyicisi bağlamı uygulama temel ve özel arama yolu gibi çeşitli yönlerini yapılandırmalarını izin verir.</span><span class="sxs-lookup"><span data-stu-id="37856-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="37856-124">`FindAssembliesByName` Yöntemi derleme çözümleme mantığı çağırmak için işlemin başlatılması CLR gerektirir.</span><span class="sxs-lookup"><span data-stu-id="37856-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="37856-125">Bu nedenle, çağırmalısınız [Coınitializeee](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (COINITEE_DEFAULT geçirme) çağırmadan önce `FindAssembliesByName`ve ardından bir çağrı izleyin [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="37856-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="37856-126">`FindAssembliesByName`döndüren bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) geçirilen derleme adı derleme bildirimi içeren dosyanın işaretçi.</span><span class="sxs-lookup"><span data-stu-id="37856-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="37856-127">Verilen derleme adı (örneğin bir sürüm içermiyorsa) tam olarak belirtilmezse, birden çok derleme döndürülen.</span><span class="sxs-lookup"><span data-stu-id="37856-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="37856-128">`FindAssembliesByName`derleme zamanında başvurulan bir derleme bulmaya çalışır bir derleyici tarafından yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37856-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37856-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37856-129">Requirements</span></span>  
 <span data-ttu-id="37856-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37856-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37856-131">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="37856-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="37856-132">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="37856-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37856-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37856-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37856-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37856-134">See Also</span></span>  
 [<span data-ttu-id="37856-135">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="37856-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="37856-136">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37856-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
