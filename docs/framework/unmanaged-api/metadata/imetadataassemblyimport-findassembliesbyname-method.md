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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b388dae0f109ff366f83c92de99b00b80bcc01a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905092"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="50797-102">IMetaDataAssemblyImport::FindAssembliesByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50797-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="50797-103">Derlemeler belirli bir dizisini alır `szAssemblyName` başvurularını çözümlemek için ortak dil çalışma zamanı (CLR) tarafından kullanılan standart kurallar kullanılarak parametre.</span><span class="sxs-lookup"><span data-stu-id="50797-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50797-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50797-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="50797-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50797-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="50797-106">[in] Belirtilen derleme için aranacak kök dizini.</span><span class="sxs-lookup"><span data-stu-id="50797-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="50797-107">Bu değer ayarlanırsa `null`, `FindAssembliesByName` yalnızca genel derleme önbelleğinde derleme için görünür.</span><span class="sxs-lookup"><span data-stu-id="50797-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="50797-108">[in] Noktalı virgül ile ayrılmış alt dizinleri (örneğin, "depo; bin2"), derleme için aranacak kök dizininin altındaki bir listesi.</span><span class="sxs-lookup"><span data-stu-id="50797-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="50797-109">Bu dizinler, varsayılan algılama kurallarını belirtilenlerin yanı sıra araştırıldığı.</span><span class="sxs-lookup"><span data-stu-id="50797-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="50797-110">[in] Bulunacak derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="50797-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="50797-111">Bu dizenin biçimi sınıf başvurusu sayfasında tanımlanan <xref:System.Reflection.AssemblyName>.</span><span class="sxs-lookup"><span data-stu-id="50797-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="50797-112">[in] Türünde bir dizi [IUnknown](/cpp/atl/iunknown) yerleştirileceği `IMetadataAssemblyImport` arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="50797-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="50797-113">[out] Yerleştirilebilir arabirim işaretçilerini sayısı `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="50797-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="50797-114">[out] Döndürülen arabirim işaretçilerini sayısı.</span><span class="sxs-lookup"><span data-stu-id="50797-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="50797-115">Diğer bir deyişle, arabirim işaretçilerini sayısı gerçekte yerleştirilen `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="50797-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50797-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="50797-116">Return Value</span></span>  
  
|<span data-ttu-id="50797-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50797-117">HRESULT</span></span>|<span data-ttu-id="50797-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50797-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="50797-119">`FindAssembliesByName` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="50797-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="50797-120">Bütünleştirilmiş kod yok vardır.</span><span class="sxs-lookup"><span data-stu-id="50797-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50797-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50797-121">Remarks</span></span>  
 <span data-ttu-id="50797-122">Bir bütünleştirilmiş kod adı verilir `FindAssembliesByName` yöntemi derleme başvurularını çözümlemek için standart kuralları izleyerek derlemeyi bulur.</span><span class="sxs-lookup"><span data-stu-id="50797-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="50797-123">(Daha fazla bilgi için [çalışma zamanı derlemeleri nasıl konumlandırır](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` derleme Çözümleyicisi bağlamı, uygulama temel ve özel arama yolu gibi çeşitli yönlerini yapılandırmak çağıranın izin verir.</span><span class="sxs-lookup"><span data-stu-id="50797-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="50797-124">`FindAssembliesByName` Yöntem CLR'nin işlemdeki bütünleştirilmiş kod çözümleme mantıksal çağırmak için başlatılması gerektirir.</span><span class="sxs-lookup"><span data-stu-id="50797-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="50797-125">Bu nedenle, çağırmalıdır [Coınitializeee](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (COINITEE_DEFAULT geçirme) çağırmadan önce `FindAssembliesByName`ve ardından bir çağrı ile izleyin [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="50797-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="50797-126">`FindAssembliesByName` döndürür bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) geçirilen derleme adı için derleme bildirimini içeren dosyayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="50797-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="50797-127">Belirtilen derleme adı tam olarak (örneğin bir sürüm içermiyorsa) belirtilmezse, birden çok derleme döndürülen.</span><span class="sxs-lookup"><span data-stu-id="50797-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="50797-128">`FindAssembliesByName` başvurulan derlemenin derleme zamanında bulmaya çalışır bir derleyici tarafından yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="50797-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50797-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50797-129">Requirements</span></span>  
 <span data-ttu-id="50797-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50797-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50797-131">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="50797-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50797-132">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="50797-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50797-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50797-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50797-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50797-134">See also</span></span>

- [<span data-ttu-id="50797-135">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="50797-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="50797-136">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50797-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
