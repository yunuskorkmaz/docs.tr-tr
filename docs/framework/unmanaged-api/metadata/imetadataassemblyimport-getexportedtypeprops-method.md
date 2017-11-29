---
title: IMetaDataAssemblyImport::GetExportedTypeProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetExportedTypeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e142d0c77493ac1e9ab2bf485d8e111af4fb3ddb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="5182e-102">IMetaDataAssemblyImport::GetExportedTypeProps Metodu</span><span class="sxs-lookup"><span data-stu-id="5182e-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="5182e-103">Belirtilen meta veri imzayla verilen türünün özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="5182e-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5182e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5182e-104">Syntax</span></span>  
  
```  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,   
    [out] LPWSTR            szName,   
    [in]  ULONG             cchName,   
    [out] ULONG             *pchName,   
    [out] mdToken           *ptkImplementation,   
    [out] mdTypeDef         *ptkTypeDef,   
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5182e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5182e-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="5182e-106">[in] Bir `mdExportedType` dışarı aktarılan türünü temsil eden meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="5182e-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="5182e-107">[out] Dışarı aktarılan türünün adı.</span><span class="sxs-lookup"><span data-stu-id="5182e-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5182e-108">[in] Geniş karakterler boyutu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="5182e-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="5182e-109">[out] Gerçekte döndürülen geniş karakter sayısı`szName`</span><span class="sxs-lookup"><span data-stu-id="5182e-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="5182e-110">[out] Bir `mdFile`, `mdAssemblyRef`, veya `mdExportedType` içeren veya erişime izin verilen türünün özelliklerini meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="5182e-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="5182e-111">[out] Bir işaretçi bir `mdTypeDef` dosyasındaki bir türü temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="5182e-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="5182e-112">[out] Dışarı aktarılan türüne uygulanacağını meta verileri açıklayan bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5182e-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="5182e-113">Bayrak değeri bir veya daha fazla olabilir [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="5182e-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5182e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5182e-114">Requirements</span></span>  
 <span data-ttu-id="5182e-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5182e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5182e-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5182e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5182e-117">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5182e-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5182e-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5182e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5182e-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5182e-119">See Also</span></span>  
 [<span data-ttu-id="5182e-120">Imetadataassemblyımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="5182e-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
