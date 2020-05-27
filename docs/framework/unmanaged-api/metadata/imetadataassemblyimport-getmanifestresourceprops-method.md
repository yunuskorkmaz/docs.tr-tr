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
ms.openlocfilehash: c0b6d53ce3be3aed6a577bf6e38a281928499848
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009034"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="50521-102">IMetaDataAssemblyImport::GetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50521-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="50521-103">Belirtilen meta veri imzasıyla bildirim kaynağının özellik kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="50521-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50521-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="50521-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="50521-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50521-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="50521-106">'ndaki `mdManifestResource`Özelliklerinin alınacağı kaynağı temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="50521-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="50521-107">dışı Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="50521-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="50521-108">'ndaki , Öğesinin geniş karakter cinsinden boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="50521-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="50521-109">dışı Aslında ' de döndürülen geniş karakter sayısının bir işaretçisi `szName` .</span><span class="sxs-lookup"><span data-stu-id="50521-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="50521-110">dışı `mdFile` `mdAssemblyRef` Kaynağı içeren, sırasıyla, dosya veya derlemeyi temsil eden belirtece veya belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="50521-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="50521-111">dışı Dosyanın içindeki kaynağın başlangıcına olan sapmayı belirten bir değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="50521-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="50521-112">dışı Bir kaynağa uygulanan meta verileri tanımlayan bayrakların işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="50521-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="50521-113">Flags değeri bir veya daha fazla [CorManifestResourceFlags](cormanifestresourceflags-enumeration.md) değeri birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="50521-113">The flags value is a combination of one or more [CorManifestResourceFlags](cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50521-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50521-114">Requirements</span></span>  
 <span data-ttu-id="50521-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50521-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50521-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="50521-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50521-117">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="50521-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50521-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50521-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50521-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50521-119">See also</span></span>

- [<span data-ttu-id="50521-120">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50521-120">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
