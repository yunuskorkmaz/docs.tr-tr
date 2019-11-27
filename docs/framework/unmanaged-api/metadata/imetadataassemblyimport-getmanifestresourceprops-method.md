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
ms.openlocfilehash: c1792ed0f15f8cfb62567593c9694453650f0bb9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436322"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="67346-102">IMetaDataAssemblyImport::GetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67346-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="67346-103">Belirtilen meta veri imzasıyla bildirim kaynağının özellik kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="67346-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67346-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67346-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="67346-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67346-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="67346-106">'ndaki Özelliklerinin alınacağı kaynağı temsil eden `mdManifestResource` belirteç.</span><span class="sxs-lookup"><span data-stu-id="67346-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="67346-107">dışı Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="67346-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="67346-108">'ndaki `szName`geniş karakter cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="67346-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="67346-109">dışı `szName`' de döndürülen geniş karakter sayısının bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="67346-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="67346-110">dışı Kaynağı içeren, sırasıyla dosyayı veya derlemeyi temsil eden bir `mdFile` belirtecinin veya `mdAssemblyRef` belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="67346-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="67346-111">dışı Dosyanın içindeki kaynağın başlangıcına olan sapmayı belirten bir değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="67346-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="67346-112">dışı Bir kaynağa uygulanan meta verileri tanımlayan bayrakların işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="67346-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="67346-113">Flags değeri bir veya daha fazla [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) değeri birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="67346-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67346-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67346-114">Requirements</span></span>  
 <span data-ttu-id="67346-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67346-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67346-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="67346-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="67346-117">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="67346-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="67346-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67346-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67346-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67346-119">See also</span></span>

- [<span data-ttu-id="67346-120">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67346-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
