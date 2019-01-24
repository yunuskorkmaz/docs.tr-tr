---
title: IMetaDataAssemblyImport::GetAssemblyRefProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91d21f51312eb812d253ba218eeeb99e5df1ff8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730236"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="e186e-102">IMetaDataAssemblyImport::GetAssemblyRefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="e186e-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="e186e-103">Belirtilen meta veri imzası olan derleme başvurusu için özellikler kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="e186e-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e186e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e186e-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="e186e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e186e-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="e186e-106">[in] `mdAssemblyRef` Derleme başvurusu özellikleri alınacağı temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="e186e-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="e186e-107">[out] Ortak anahtarı veya meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e186e-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="e186e-108">[out] Döndürülen bir ortak anahtar veya belirteç bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="e186e-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="e186e-109">[out] Derlemenin basit adını.</span><span class="sxs-lookup"><span data-stu-id="e186e-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="e186e-110">[in] Geniş karakter, boyutunu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="e186e-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="e186e-111">[out] Gerçekte döndürülen geniş karakter sayısı için bir işaretçi `szName`.</span><span class="sxs-lookup"><span data-stu-id="e186e-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="e186e-112">[out] Derleme meta verileri içeren bir ASSEMBLYMETADATA yapısı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e186e-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="e186e-113">[out] Karma değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e186e-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="e186e-114">Bu, SHA-1 algoritmasını kullanan karma `PublicKey` arfFullOriginator bayrak sürece, başvurulan derleme özelliği [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) numaralandırma ayarı.</span><span class="sxs-lookup"><span data-stu-id="e186e-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="e186e-115">[out] Döndürülen karma değeri geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="e186e-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="e186e-116">[out] Bir derlemeye uygulanan meta verileri açıklayan bayrakları için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e186e-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="e186e-117">Bir veya daha fazla flags değeri birleşimidir [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="e186e-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e186e-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e186e-118">Return Value</span></span>  
 <span data-ttu-id="e186e-119">Bu yöntem başarılı olursa başarılıysa S_OK döndürür; Aksi takdirde wınerror üstbilgi dosyasında tanımlanan hata kodlarından birini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e186e-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e186e-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e186e-120">Requirements</span></span>  
 <span data-ttu-id="e186e-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e186e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e186e-122">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="e186e-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e186e-123">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="e186e-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e186e-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e186e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e186e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e186e-125">See also</span></span>
- [<span data-ttu-id="e186e-126">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e186e-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
