---
description: ': IMetaDataAssemblyImport:: GetManifestResourceProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d8f390f8eede5153df282cc30479ceff22fb552d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728294"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="89ade-103">IMetaDataAssemblyImport::GetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89ade-103">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>

<span data-ttu-id="89ade-104">Belirtilen meta veri imzasıyla bildirim kaynağının özellik kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="89ade-104">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89ade-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89ade-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="89ade-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89ade-106">Parameters</span></span>  

 `mdmr`  
 <span data-ttu-id="89ade-107">'ndaki `mdManifestResource` Özelliklerinin alınacağı kaynağı temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="89ade-107">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="89ade-108">dışı Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="89ade-108">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="89ade-109">'ndaki , Öğesinin geniş karakter cinsinden boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="89ade-109">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="89ade-110">dışı Aslında ' de döndürülen geniş karakter sayısının bir işaretçisi `szName` .</span><span class="sxs-lookup"><span data-stu-id="89ade-110">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="89ade-111">dışı `mdFile` `mdAssemblyRef` Kaynağı içeren, sırasıyla, dosya veya derlemeyi temsil eden belirtece veya belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="89ade-111">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="89ade-112">dışı Dosyanın içindeki kaynağın başlangıcına olan sapmayı belirten bir değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="89ade-112">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="89ade-113">dışı Bir kaynağa uygulanan meta verileri tanımlayan bayrakların işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="89ade-113">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="89ade-114">Flags değeri bir veya daha fazla [CorManifestResourceFlags](cormanifestresourceflags-enumeration.md) değeri birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="89ade-114">The flags value is a combination of one or more [CorManifestResourceFlags](cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89ade-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89ade-115">Requirements</span></span>  

 <span data-ttu-id="89ade-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89ade-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89ade-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="89ade-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89ade-118">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="89ade-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89ade-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89ade-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89ade-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89ade-120">See also</span></span>

- [<span data-ttu-id="89ade-121">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89ade-121">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
