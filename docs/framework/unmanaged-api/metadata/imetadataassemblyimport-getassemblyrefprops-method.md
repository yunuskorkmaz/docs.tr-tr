---
title: IMetaDataAssemblyImport::GetAssemblyRefProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetAssemblyRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76ae1d81db314530ab33a42cb99824da1745dff0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="c6169-102">IMetaDataAssemblyImport::GetAssemblyRefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="c6169-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="c6169-103">Belirtilen meta veri imzayla derleme başvurusu için özellikler kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="c6169-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6169-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6169-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,   
    [out] const void          **ppbPublicKeyOrToken,   
    [out] ULONG                *pcbPublicKeyOrToken,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] ASSEMBLYMETADATA     *pMetaData,   
    [out] const void           **ppbHashValue,   
    [out] ULONG                *pcbHashValue,   
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6169-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6169-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="c6169-106">[in] `mdAssemblyRef` Özellikleri almak istediğiniz derleme başvurusunu gösteren meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="c6169-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="c6169-107">[out] Ortak anahtar veya meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c6169-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="c6169-108">[out] Döndürülen bir ortak anahtar ya da belirteci bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="c6169-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="c6169-109">[out] Derleme basit adı.</span><span class="sxs-lookup"><span data-stu-id="c6169-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c6169-110">[in] Geniş karakter boyutu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="c6169-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="c6169-111">[out] Gerçekte döndürülen geniş karakter sayısını gösteren bir işaretçi `szName`.</span><span class="sxs-lookup"><span data-stu-id="c6169-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="c6169-112">[out] Derleme meta verilerini içeren bir ASSEMBLYMETADATA yapısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c6169-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="c6169-113">[out] Karma değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c6169-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="c6169-114">SHA-1 algoritmasını kullanan karma budur `PublicKey` arfFullOriginator bayrak sürece, başvurulan derleme özelliğinin [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) numaralandırma ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c6169-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="c6169-115">[out] Döndürülen karma değeri geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="c6169-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="c6169-116">[out] Bir derlemeye uygulanan meta verileri açıklayan bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c6169-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="c6169-117">Bir veya birden çok bayrak değeri birleşimidir [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="c6169-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6169-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c6169-118">Return Value</span></span>  
 <span data-ttu-id="c6169-119">Bu yöntem başarılı olursa S_OK döndürür; Aksi takdirde, bu Winerror.h'de üstbilgi dosyasında tanımlanan hata kodlarından birini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6169-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6169-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6169-120">Requirements</span></span>  
 <span data-ttu-id="c6169-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6169-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6169-122">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c6169-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c6169-123">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c6169-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6169-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6169-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6169-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6169-125">See Also</span></span>  
 [<span data-ttu-id="c6169-126">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6169-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
