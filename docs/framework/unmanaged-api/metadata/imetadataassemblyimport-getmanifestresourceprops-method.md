---
title: IMetaDataAssemblyImport::GetManifestResourceProps Yöntemi
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
ms.openlocfilehash: d87d0d46ede65cf44c84edba92fe246174088a4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177656"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="7ec71-102">IMetaDataAssemblyImport::GetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ec71-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="7ec71-103">Belirtilen meta veri imzasıyla bildirim kaynağının özellikleri kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="7ec71-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ec71-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ec71-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="7ec71-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ec71-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="7ec71-106">[içinde] Özellikleri `mdManifestResource` almak için kaynağı temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="7ec71-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="7ec71-107">[çıkış] Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="7ec71-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="7ec71-108">[içinde] Boyutu, geniş chars, `szName`ve .</span><span class="sxs-lookup"><span data-stu-id="7ec71-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="7ec71-109">[çıkış] Geniş karakter sayısına işaretçi aslında `szName`döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7ec71-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="7ec71-110">[çıkış] Kaynağı içeren `mdFile` dosya yı `mdAssemblyRef` veya derlemeyi temsil eden bir belirteç veya belirteç için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7ec71-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="7ec71-111">[çıkış] Dosya içindeki kaynağın başına mahsup belirten bir değer için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7ec71-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="7ec71-112">[çıkış] Kaynağa uygulanan meta verileri açıklayan bayraklar için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7ec71-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="7ec71-113">Bayrak değeri, bir veya daha fazla [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) değerinin bir leşimidir.</span><span class="sxs-lookup"><span data-stu-id="7ec71-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ec71-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ec71-114">Requirements</span></span>  
 <span data-ttu-id="7ec71-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ec71-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ec71-116">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7ec71-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7ec71-117">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="7ec71-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7ec71-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ec71-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec71-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ec71-119">See also</span></span>

- [<span data-ttu-id="7ec71-120">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ec71-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
