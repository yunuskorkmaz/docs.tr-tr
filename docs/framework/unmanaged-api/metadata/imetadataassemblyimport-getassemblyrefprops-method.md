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
ms.openlocfilehash: 9aef471c1155070af0e9bcca14975a65bc5dc763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175973"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="43a96-102">IMetaDataAssemblyImport::GetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43a96-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="43a96-103">Belirtilen meta veri imzasıyla derleme başvurusu için özellik kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="43a96-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43a96-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43a96-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="43a96-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43a96-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="43a96-106">[içinde] Özellikleri `mdAssemblyRef` almak için derleme başvurutemsil meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="43a96-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="43a96-107">[çıkış] Ortak anahtarveya meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="43a96-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="43a96-108">[çıkış] Döndürülen ortak anahtar veya belirteçteki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="43a96-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="43a96-109">[çıkış] Derlemenin basit adı.</span><span class="sxs-lookup"><span data-stu-id="43a96-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="43a96-110">[içinde] Boyutu, geniş chars, `szName`ve .</span><span class="sxs-lookup"><span data-stu-id="43a96-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="43a96-111">[çıkış] Geniş karakter sayısına işaretçi aslında `szName`döndürülür.</span><span class="sxs-lookup"><span data-stu-id="43a96-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="43a96-112">[çıkış] Derleme meta verilerini içeren bir ASSEMBLYMETADATA yapısına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="43a96-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="43a96-113">[çıkış] Karma değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="43a96-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="43a96-114">Bu, Sha-1 algoritmasını kullanarak, `PublicKey` [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) numaralandırmasının arfFullOriginator bayrağı ayarlanmadığı sürece, başvurulan derleme özelliğinin karmadır.</span><span class="sxs-lookup"><span data-stu-id="43a96-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="43a96-115">[çıkış] Döndürülen karma değerdeki geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="43a96-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="43a96-116">[çıkış] Bir derlemeye uygulanan meta verileri açıklayan bayraklar için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="43a96-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="43a96-117">Bayrak değeri, bir veya daha fazla [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerinin bir leşimidir.</span><span class="sxs-lookup"><span data-stu-id="43a96-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43a96-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="43a96-118">Return Value</span></span>  
 <span data-ttu-id="43a96-119">Bu yöntem başarılı olursa S_OK döndürür; aksi takdirde, Winerror.h üstbilgi dosyasında tanımlanan hata kodlarından birini döndürür.</span><span class="sxs-lookup"><span data-stu-id="43a96-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43a96-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43a96-120">Requirements</span></span>  
 <span data-ttu-id="43a96-121">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43a96-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43a96-122">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="43a96-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="43a96-123">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="43a96-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="43a96-124">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43a96-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43a96-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43a96-125">See also</span></span>

- [<span data-ttu-id="43a96-126">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43a96-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
