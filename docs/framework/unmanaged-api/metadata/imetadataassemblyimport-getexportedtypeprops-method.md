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
ms.openlocfilehash: 82302124828a2dab73b445128d7d847e112edd36
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448211"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="d2342-102">IMetaDataAssemblyImport::GetExportedTypeProps Metodu</span><span class="sxs-lookup"><span data-stu-id="d2342-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="d2342-103">Belirtilen meta veri imzasıyla, dışarıya aktarılmış türün özelliklerinin kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="d2342-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2342-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2342-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d2342-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d2342-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="d2342-106">'ndaki Bir `mdExportedType` meta veri belirteci, dışarıya aktarılmış türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d2342-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="d2342-107">dışı İçe aktarılmış türün adı.</span><span class="sxs-lookup"><span data-stu-id="d2342-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d2342-108">'ndaki `szName`geniş karakterdeki boyut.</span><span class="sxs-lookup"><span data-stu-id="d2342-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="d2342-109">dışı `szName` ' de döndürülen geniş karakter sayısı</span><span class="sxs-lookup"><span data-stu-id="d2342-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="d2342-110">dışı `mdFile`, `mdAssemblyRef`veya bir `mdExportedType` meta veri belirteci, ancak bu, içe aktarılmış türün özelliklerine erişim izni verir.</span><span class="sxs-lookup"><span data-stu-id="d2342-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="d2342-111">dışı Dosyadaki bir türü temsil eden `mdTypeDef` belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d2342-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="d2342-112">dışı İçe aktarılmış türe uygulanan meta verileri tanımlayan bayrakların işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d2342-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="d2342-113">Bayrak değeri bir veya daha fazla [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2342-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2342-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2342-114">Requirements</span></span>  
 <span data-ttu-id="d2342-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2342-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2342-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d2342-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2342-117">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d2342-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d2342-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2342-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2342-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2342-119">See also</span></span>

- [<span data-ttu-id="d2342-120">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2342-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
