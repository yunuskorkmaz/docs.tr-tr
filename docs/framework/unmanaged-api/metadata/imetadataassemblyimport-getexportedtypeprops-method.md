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
ms.openlocfilehash: c76e46c75680d9fc0ad70e94da288f0c6b5e5ee1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446326"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="54adb-102">IMetaDataAssemblyImport::GetExportedTypeProps Metodu</span><span class="sxs-lookup"><span data-stu-id="54adb-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="54adb-103">Belirtilen meta veri imzayla verilen türünün özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="54adb-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54adb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54adb-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="54adb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54adb-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="54adb-106">[in] Bir `mdExportedType` dışarı aktarılan türünü temsil eden meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="54adb-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="54adb-107">[out] Dışarı aktarılan türünün adı.</span><span class="sxs-lookup"><span data-stu-id="54adb-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="54adb-108">[in] Geniş karakterler boyutu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="54adb-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="54adb-109">[out] Gerçekte döndürülen geniş karakter sayısı `szName`</span><span class="sxs-lookup"><span data-stu-id="54adb-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="54adb-110">[out] Bir `mdFile`, `mdAssemblyRef`, veya `mdExportedType` içeren veya erişime izin verilen türünün özelliklerini meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="54adb-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="54adb-111">[out] Bir işaretçi bir `mdTypeDef` dosyasındaki bir türü temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="54adb-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="54adb-112">[out] Dışarı aktarılan türüne uygulanacağını meta verileri açıklayan bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="54adb-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="54adb-113">Bayrak değeri bir veya daha fazla olabilir [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="54adb-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54adb-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54adb-114">Requirements</span></span>  
 <span data-ttu-id="54adb-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54adb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54adb-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="54adb-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54adb-117">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="54adb-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="54adb-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54adb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54adb-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54adb-119">See Also</span></span>  
 [<span data-ttu-id="54adb-120">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54adb-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
