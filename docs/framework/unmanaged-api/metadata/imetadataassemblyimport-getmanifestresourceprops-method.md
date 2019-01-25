---
title: IMetaDataAssemblyImport::GetManifestResourceProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5bad338777db2097ed72ce327f42fde0f0db58e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693723"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="4c75b-102">IMetaDataAssemblyImport::GetManifestResourceProps Metodu</span><span class="sxs-lookup"><span data-stu-id="4c75b-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="4c75b-103">Belirtilen meta veri imzası bildirim kaynak özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="4c75b-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c75b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c75b-104">Syntax</span></span>  
  
```  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] mdToken              *ptkImplementation,   
    [out] DWORD                *pdwOffset,   
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c75b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c75b-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="4c75b-106">[in] Bir `mdManifestResource` özelliklerini alınacağı kaynak temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="4c75b-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="4c75b-107">[out] Kaynak adı.</span><span class="sxs-lookup"><span data-stu-id="4c75b-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="4c75b-108">[in] Geniş karakter, boyutunu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="4c75b-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="4c75b-109">[out] Gerçekte döndürülen geniş karakter sayısı için bir işaretçi `szName`.</span><span class="sxs-lookup"><span data-stu-id="4c75b-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="4c75b-110">[out] Bir işaretçi bir `mdFile` belirteç veya `mdAssemblyRef` içeren kaynak dosya veya derleme, sırasıyla temsil eden belirteç.</span><span class="sxs-lookup"><span data-stu-id="4c75b-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="4c75b-111">[out] Kaynak dosyası içinde başlangıcına uzaklık belirten bir değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4c75b-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="4c75b-112">[out] Bir kaynağa uygulanan meta verileri açıklayan bayrakları için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4c75b-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="4c75b-113">Bir veya daha fazla flags değeri birleşimidir [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="4c75b-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c75b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c75b-114">Requirements</span></span>  
 <span data-ttu-id="4c75b-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c75b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c75b-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4c75b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c75b-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="4c75b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4c75b-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c75b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c75b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c75b-119">See also</span></span>
- [<span data-ttu-id="4c75b-120">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c75b-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
