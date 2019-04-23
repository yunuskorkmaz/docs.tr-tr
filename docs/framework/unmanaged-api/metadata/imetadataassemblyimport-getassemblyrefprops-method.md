---
title: IMetaDataAssemblyImport::GetAssemblyRefProps Yöntemi
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
ms.openlocfilehash: e6c550ff7af2dda8bc06afd771024fe290339904
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089789"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="37bb6-102">IMetaDataAssemblyImport::GetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37bb6-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="37bb6-103">Belirtilen meta veri imzası olan derleme başvurusu için özellikler kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="37bb6-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37bb6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37bb6-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="37bb6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="37bb6-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="37bb6-106">[in] `mdAssemblyRef` Derleme başvurusu özellikleri alınacağı temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="37bb6-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="37bb6-107">[out] Ortak anahtarı veya meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="37bb6-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="37bb6-108">[out] Döndürülen bir ortak anahtar veya belirteç bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="37bb6-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="37bb6-109">[out] Derlemenin basit adını.</span><span class="sxs-lookup"><span data-stu-id="37bb6-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="37bb6-110">[in] Geniş karakter, boyutunu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="37bb6-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="37bb6-111">[out] Gerçekte döndürülen geniş karakter sayısı için bir işaretçi `szName`.</span><span class="sxs-lookup"><span data-stu-id="37bb6-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="37bb6-112">[out] Derleme meta verileri içeren bir ASSEMBLYMETADATA yapısı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="37bb6-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="37bb6-113">[out] Karma değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="37bb6-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="37bb6-114">Bu, SHA-1 algoritmasını kullanan karma `PublicKey` arfFullOriginator bayrak sürece, başvurulan derleme özelliği [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) numaralandırma ayarı.</span><span class="sxs-lookup"><span data-stu-id="37bb6-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="37bb6-115">[out] Döndürülen karma değeri geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="37bb6-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="37bb6-116">[out] Bir derlemeye uygulanan meta verileri açıklayan bayrakları için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="37bb6-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="37bb6-117">Bir veya daha fazla flags değeri birleşimidir [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="37bb6-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37bb6-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="37bb6-118">Return Value</span></span>  
 <span data-ttu-id="37bb6-119">Bu yöntem başarılı olursa başarılıysa S_OK döndürür; Aksi takdirde wınerror üstbilgi dosyasında tanımlanan hata kodlarından birini döndürür.</span><span class="sxs-lookup"><span data-stu-id="37bb6-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37bb6-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37bb6-120">Requirements</span></span>  
 <span data-ttu-id="37bb6-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37bb6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37bb6-122">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="37bb6-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="37bb6-123">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="37bb6-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37bb6-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37bb6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37bb6-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37bb6-125">See also</span></span>

- [<span data-ttu-id="37bb6-126">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37bb6-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
