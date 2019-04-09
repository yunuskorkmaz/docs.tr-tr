---
title: IMetaDataAssemblyEmit::DefineExportedType Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e89fda72371f197efeeeef8f31ec396c334cfcb2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122037"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="ea238-102">IMetaDataAssemblyEmit::DefineExportedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea238-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="ea238-103">Oluşturur bir `ExportedType` yapısı meta verilerini içeren, belirtilen dışarı türü ve ilişkili meta veri belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="ea238-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea238-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea238-104">Syntax</span></span>  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea238-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea238-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="ea238-106">[in] Dışa aktarılacak tür adı.</span><span class="sxs-lookup"><span data-stu-id="ea238-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="ea238-107">Sürüm 1.1 ortak dil çalışma zamanının dışarı aktarılan tür adı verilen ad tam eşleşmelidir `TypeDef` türü.</span><span class="sxs-lookup"><span data-stu-id="ea238-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="ea238-108">[in] Dışarı aktarılan tür burada uygulanan belirten bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="ea238-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="ea238-109">Geçerli değerler ve bunların ilişkili anlamları vardır:</span><span class="sxs-lookup"><span data-stu-id="ea238-109">The valid values and their associated meanings are:</span></span>  
  
-   `mdFile` <span data-ttu-id="ea238-110">Bu derleme içinde farklı bir dosya türü uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ea238-110">The type is implemented in a different file within this assembly.</span></span>  
  
-   `mdAssemblyRef` <span data-ttu-id="ea238-111">Türü farklı bir derlemede uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ea238-111">The type is implemented in a different assembly.</span></span>  
  
-   `mdExportedTYpe` <span data-ttu-id="ea238-112">Tür, başka bir tür içinde yer alıyor.</span><span class="sxs-lookup"><span data-stu-id="ea238-112">The type is nested within some other type.</span></span>  
  
-   `mdFileNil` <span data-ttu-id="ea238-113">Türü, bildirim olarak aynı dosya ve iç içe geçmiş bir tür değil.</span><span class="sxs-lookup"><span data-stu-id="ea238-113">The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="ea238-114">[in] Bir belirteci meta veri dışarı aktarılmasına izin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea238-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="ea238-115">İçinde bu değer girilir `TypeDef` tablo dosyanızda türün uyguladığı ve yalnızca bu dosya bu derlemede olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ea238-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="ea238-116">[in] Bitsel bir birleşimi [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) özellik ayarları dışarı aktarılan türü tanımlayan sabit listesi değerleri.</span><span class="sxs-lookup"><span data-stu-id="ea238-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="ea238-117">[out] Dışarı aktarılan tür gösteren döndürülen meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ea238-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea238-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea238-118">Remarks</span></span>  
 <span data-ttu-id="ea238-119">Bir `ExportedType` meta veri yapısı, bu derleme tarafından kullanıma sunulan ve bildirimini içeren farklı bir modül içinde uygulanan her türü için tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ea238-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea238-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea238-120">Requirements</span></span>  
 <span data-ttu-id="ea238-121">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea238-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea238-122">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ea238-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea238-123">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="ea238-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="ea238-124">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ea238-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ea238-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea238-125">See also</span></span>

- [<span data-ttu-id="ea238-126">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea238-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
