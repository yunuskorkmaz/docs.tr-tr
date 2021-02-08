---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyImport:: GetExportedTypeProps yöntemi'
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
ms.openlocfilehash: 894fb65fb6de76a218489b2a85a2d3c20c572789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784125"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="a0516-103">IMetaDataAssemblyImport::GetExportedTypeProps Metodu</span><span class="sxs-lookup"><span data-stu-id="a0516-103">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>

<span data-ttu-id="a0516-104">Belirtilen meta veri imzasıyla, dışarıya aktarılmış türün özelliklerinin kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="a0516-104">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0516-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0516-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a0516-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a0516-106">Parameters</span></span>  

 `mdct`  
 <span data-ttu-id="a0516-107">'ndaki `mdExportedType` İçe aktarılmış türü temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="a0516-107">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="a0516-108">dışı İçe aktarılmış türün adı.</span><span class="sxs-lookup"><span data-stu-id="a0516-108">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="a0516-109">'ndaki Öğesinin geniş karakterdeki boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="a0516-109">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="a0516-110">dışı Aslında içinde döndürülen geniş karakter sayısı `szName`</span><span class="sxs-lookup"><span data-stu-id="a0516-110">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="a0516-111">dışı Bir `mdFile` , `mdAssemblyRef` veya, bir veya daha fazla `mdExportedType` içe aktarılmış türün özelliklerine erişim izni veren bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="a0516-111">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="a0516-112">dışı `mdTypeDef` Dosyadaki bir türü temsil eden belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a0516-112">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="a0516-113">dışı İçe aktarılmış türe uygulanan meta verileri tanımlayan bayrakların işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a0516-113">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="a0516-114">Bayrak değeri bir veya daha fazla [CorTypeAttr](cortypeattr-enumeration.md) değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="a0516-114">The flags value can be one or more [CorTypeAttr](cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0516-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0516-115">Requirements</span></span>  

 <span data-ttu-id="a0516-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0516-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0516-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a0516-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0516-118">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a0516-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0516-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0516-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0516-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0516-120">See also</span></span>

- [<span data-ttu-id="a0516-121">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a0516-121">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
