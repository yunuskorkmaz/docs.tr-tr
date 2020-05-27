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
ms.openlocfilehash: 944941c2356cae93ecc85f1714b4b29aefcb50ad
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008410"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="0fe74-102">IMetaDataAssemblyImport::GetExportedTypeProps Metodu</span><span class="sxs-lookup"><span data-stu-id="0fe74-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="0fe74-103">Belirtilen meta veri imzasıyla, dışarıya aktarılmış türün özelliklerinin kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="0fe74-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fe74-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0fe74-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0fe74-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0fe74-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="0fe74-106">'ndaki `mdExportedType`İçe aktarılmış türü temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="0fe74-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="0fe74-107">dışı İçe aktarılmış türün adı.</span><span class="sxs-lookup"><span data-stu-id="0fe74-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="0fe74-108">'ndaki Öğesinin geniş karakterdeki boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="0fe74-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="0fe74-109">dışı Aslında içinde döndürülen geniş karakter sayısı`szName`</span><span class="sxs-lookup"><span data-stu-id="0fe74-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="0fe74-110">dışı Bir `mdFile` , `mdAssemblyRef` veya, bir veya daha fazla `mdExportedType` içe aktarılmış türün özelliklerine erişim izni veren bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="0fe74-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="0fe74-111">dışı `mdTypeDef`Dosyadaki bir türü temsil eden belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0fe74-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="0fe74-112">dışı İçe aktarılmış türe uygulanan meta verileri tanımlayan bayrakların işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0fe74-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="0fe74-113">Bayrak değeri bir veya daha fazla [CorTypeAttr](cortypeattr-enumeration.md) değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="0fe74-113">The flags value can be one or more [CorTypeAttr](cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fe74-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0fe74-114">Requirements</span></span>  
 <span data-ttu-id="0fe74-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fe74-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fe74-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0fe74-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0fe74-117">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0fe74-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0fe74-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fe74-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fe74-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fe74-119">See also</span></span>

- [<span data-ttu-id="0fe74-120">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0fe74-120">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
