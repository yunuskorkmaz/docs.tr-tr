---
title: IMetaDataAssemblyImport::GetAssemblyProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 911d0d1444e2cf3cb8241eeeff63a5a86b4ab806
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446280"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="01961-102">IMetaDataAssemblyImport::GetAssemblyProps Metodu</span><span class="sxs-lookup"><span data-stu-id="01961-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="01961-103">Belirtilen meta veri imzayla derleme için özellikler kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="01961-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01961-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01961-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01961-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01961-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="01961-106">[in].</span><span class="sxs-lookup"><span data-stu-id="01961-106">[in].</span></span> <span data-ttu-id="01961-107">`mdAssembly` Özellikleri almak istediğiniz bütünleştirilmiş kod gösteren meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="01961-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="01961-108">[out] Ortak anahtar veya meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="01961-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="01961-109">[out] Döndürülen ortak anahtar bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="01961-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="01961-110">[out] Derleme dosyalarında karması için kullanılan algoritma için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="01961-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="01961-111">[out] Derleme basit adı.</span><span class="sxs-lookup"><span data-stu-id="01961-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="01961-112">[in] Geniş karakter boyutu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="01961-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="01961-113">[out] Gerçekte döndürülen geniş karakter sayısı `szName`.</span><span class="sxs-lookup"><span data-stu-id="01961-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="01961-114">[out] Derleme meta verilerini içeren bir ASSEMBLYMETADATA yapısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="01961-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="01961-115">[out] Bir derlemeye uygulanan meta verileri açıklayan bayrakları.</span><span class="sxs-lookup"><span data-stu-id="01961-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="01961-116">Bu değer bir veya daha fazla birleşimidir [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="01961-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01961-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01961-117">Requirements</span></span>  
 <span data-ttu-id="01961-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01961-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01961-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="01961-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01961-120">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="01961-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="01961-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01961-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01961-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01961-122">See Also</span></span>  
 [<span data-ttu-id="01961-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01961-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
