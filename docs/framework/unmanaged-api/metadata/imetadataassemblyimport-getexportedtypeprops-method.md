---
title: IMetaDataAssemblyImport::GetExportedTypeProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e222f1a39276b6debc348bfb25e8db65cb648ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544646"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="b2b33-102">IMetaDataAssemblyImport::GetExportedTypeProps Metodu</span><span class="sxs-lookup"><span data-stu-id="b2b33-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="b2b33-103">Belirtilen meta veri imzası ile verilen tür özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="b2b33-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2b33-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2b33-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="b2b33-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2b33-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="b2b33-106">[in] Bir `mdExportedType` dışarı aktarılan tür temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="b2b33-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="b2b33-107">[out] Dışarı aktarılan tür adı.</span><span class="sxs-lookup"><span data-stu-id="b2b33-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b2b33-108">[in] Geniş karakter cinsinden boyutu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="b2b33-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b2b33-109">[out] Gerçekte döndürülen geniş karakter sayısı `szName`</span><span class="sxs-lookup"><span data-stu-id="b2b33-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="b2b33-110">[out] Bir `mdFile`, `mdAssemblyRef`, veya `mdExportedType` içeren veya erişime izin verilen tür özelliklerini meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="b2b33-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="b2b33-111">[out] Bir işaretçi bir `mdTypeDef` dosyasındaki türünü temsil eden belirteç.</span><span class="sxs-lookup"><span data-stu-id="b2b33-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="b2b33-112">[out] Dışarı aktarılan türe uygulandı meta verileri açıklayan bayrakları için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b2b33-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="b2b33-113">Flags değeri bir veya daha fazla [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="b2b33-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2b33-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2b33-114">Requirements</span></span>  
 <span data-ttu-id="b2b33-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2b33-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2b33-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b2b33-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2b33-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="b2b33-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2b33-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2b33-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b33-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2b33-119">See also</span></span>
- [<span data-ttu-id="b2b33-120">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2b33-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
