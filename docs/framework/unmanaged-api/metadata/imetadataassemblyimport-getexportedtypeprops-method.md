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
ms.openlocfilehash: 15b58e01d4ce99f19f510c760819471b84380b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177767"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="5965b-102">IMetaDataAssemblyImport::GetExportedTypeProps Metodu</span><span class="sxs-lookup"><span data-stu-id="5965b-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="5965b-103">Belirtilen meta veri imzasıyla dışa aktarılan türdeki özellikler kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="5965b-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5965b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5965b-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="5965b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5965b-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="5965b-106">[içinde] Dışa aktarılan türü temsil eden `mdExportedType` bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="5965b-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="5965b-107">[çıkış] Dışa aktarılan türün adı.</span><span class="sxs-lookup"><span data-stu-id="5965b-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5965b-108">[içinde] Boyutu, geniş karakterler, . `szName`</span><span class="sxs-lookup"><span data-stu-id="5965b-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="5965b-109">[çıkış] Dönen geniş karakter sayısı`szName`</span><span class="sxs-lookup"><span data-stu-id="5965b-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="5965b-110">[çıkış] Dışa `mdAssemblyRef`aktarılan `mdExportedType` türdeki özellikleri içeren veya erişime izin veren bir `mdFile`, veya meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="5965b-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="5965b-111">[çıkış] Dosyadaki bir `mdTypeDef` türü temsil eden bir belirteç için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5965b-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="5965b-112">[çıkış] Dışa aktarılan türe uygulanan meta verileri açıklayan bayraklar için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5965b-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="5965b-113">Bayrak değeri bir veya daha fazla [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="5965b-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5965b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5965b-114">Requirements</span></span>  
 <span data-ttu-id="5965b-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5965b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5965b-116">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5965b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5965b-117">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5965b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5965b-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5965b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5965b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5965b-119">See also</span></span>

- [<span data-ttu-id="5965b-120">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5965b-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
