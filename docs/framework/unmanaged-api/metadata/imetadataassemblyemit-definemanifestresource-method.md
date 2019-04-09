---
title: IMetaDataAssemblyEmit::DefineManifestResource Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b617e29e2df22b59114c8b978daa645de1cc6176
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186725"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="a83c1-102">IMetaDataAssemblyEmit::DefineManifestResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a83c1-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="a83c1-103">Oluşturur bir `ManifestResource` belirtilen bildirim kaynağı için meta veriler içeren yapı ve ilişkili meta veri belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="a83c1-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a83c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a83c1-104">Syntax</span></span>  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a83c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a83c1-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="a83c1-106">[in] Kaynak adı.</span><span class="sxs-lookup"><span data-stu-id="a83c1-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="a83c1-107">[in] Türü bir meta veri belirteci `mdtFile` veya `mdtAssemblyRef` kaynak sağlayıcıya eşler.</span><span class="sxs-lookup"><span data-stu-id="a83c1-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="a83c1-108">Bir NULL değer, dosyanın meta verileri, katıştırılmış kaynak sağlayıcısı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a83c1-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="a83c1-109">[in] Kaynak dosyası içinde başlangıcına uzaklık.</span><span class="sxs-lookup"><span data-stu-id="a83c1-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="a83c1-110">Tek başına dosyalarındaki kaynaklar için bu her zaman sıfır olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a83c1-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="a83c1-111">Bir PE (taşınabilir çalıştırılabilir) dosyasında katıştırılmış kaynak, bir uzaklık cor.h üstbilgi dosyasında belirtilen konumda başlatan BLOB kaynağının budur.</span><span class="sxs-lookup"><span data-stu-id="a83c1-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="a83c1-112">[in] Kaynak tanımı özellik ayarlarını belirten bayrağı değerlerinin Bitsel bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="a83c1-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="a83c1-113">[out] Döndürülen meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a83c1-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a83c1-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a83c1-114">Remarks</span></span>  
 <span data-ttu-id="a83c1-115">Bir `ManifestResource` meta veri yapısı, her derlemenin dosyalarının uygulanan her bir kaynak için tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a83c1-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a83c1-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a83c1-116">Requirements</span></span>  
 <span data-ttu-id="a83c1-117">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a83c1-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a83c1-118">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a83c1-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a83c1-119">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="a83c1-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="a83c1-120">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="a83c1-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a83c1-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a83c1-121">See also</span></span>

- [<span data-ttu-id="a83c1-122">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a83c1-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
