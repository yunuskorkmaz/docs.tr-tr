---
title: IMetaDataAssemblyImport::GetAssemblyProps Yöntemi
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
ms.openlocfilehash: 4817a62d276bfdb50bfcbf658f40f5568673bea0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905053"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="1438c-102">IMetaDataAssemblyImport::GetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1438c-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="1438c-103">Belirtilen meta veri imzası ile derleme için özellikler kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="1438c-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1438c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1438c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1438c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1438c-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="1438c-106">[in].</span><span class="sxs-lookup"><span data-stu-id="1438c-106">[in].</span></span> <span data-ttu-id="1438c-107">`mdAssembly` Özelliklerini alınacağı derlemeyi temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="1438c-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="1438c-108">[out] Ortak anahtarı veya meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1438c-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="1438c-109">[out] Döndürülen ortak anahtarı bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="1438c-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="1438c-110">[out] Derleme dosyaları karma yapmak için kullanılan algoritma için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1438c-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="1438c-111">[out] Derlemenin basit adını.</span><span class="sxs-lookup"><span data-stu-id="1438c-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1438c-112">[in] Geniş karakter, boyutunu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="1438c-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="1438c-113">[out] Gerçekte döndürülen geniş karakter sayısını `szName`.</span><span class="sxs-lookup"><span data-stu-id="1438c-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="1438c-114">[out] Derleme meta verileri içeren bir ASSEMBLYMETADATA yapısı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1438c-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="1438c-115">[out] Bir derlemeye uygulanan meta verileri tanımlayan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="1438c-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="1438c-116">Bu değer bir veya daha fazla birleşimidir [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="1438c-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1438c-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1438c-117">Requirements</span></span>  
 <span data-ttu-id="1438c-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1438c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1438c-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1438c-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1438c-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="1438c-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1438c-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1438c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1438c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1438c-122">See also</span></span>

- [<span data-ttu-id="1438c-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1438c-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
