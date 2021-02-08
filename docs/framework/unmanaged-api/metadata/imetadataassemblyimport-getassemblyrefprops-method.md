---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyImport:: GetAssemblyRefProps Yöntemi'
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
ms.openlocfilehash: f7011806920ba37ca84b1a48f12da3a5557fa464
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784138"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="d1188-103">IMetaDataAssemblyImport::GetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1188-103">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>

<span data-ttu-id="d1188-104">Belirtilen meta veri imzasıyla derleme başvurusunun özellik kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="d1188-104">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1188-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1188-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d1188-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1188-106">Parameters</span></span>  

 `mdar`  
 <span data-ttu-id="d1188-107">'ndaki `mdAssemblyRef` Özelliklerinin alınacağı derleme başvurusunu temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="d1188-107">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="d1188-108">dışı Ortak anahtara veya meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d1188-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="d1188-109">dışı Döndürülen ortak anahtar veya belirteçteki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="d1188-109">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="d1188-110">dışı Derlemenin basit adı.</span><span class="sxs-lookup"><span data-stu-id="d1188-110">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d1188-111">'ndaki , Öğesinin geniş karakter cinsinden boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="d1188-111">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="d1188-112">dışı Aslında ' de döndürülen geniş karakter sayısının bir işaretçisi `szName` .</span><span class="sxs-lookup"><span data-stu-id="d1188-112">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="d1188-113">dışı Derleme meta verilerini içeren bir ASSEMBLYMETADATA yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d1188-113">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="d1188-114">dışı Karma değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d1188-114">[out] A pointer to the hash value.</span></span> <span data-ttu-id="d1188-115">Bu, `PublicKey` [AssemblyRefFlags](assemblyrefflags-enumeration.md) numaralandırması Için arfFullOriginator bayrağı ayarlanmadığı takdirde, başvurulan derlemenin özelliğinin SHA-1 algoritmasını kullanan karmadır.</span><span class="sxs-lookup"><span data-stu-id="d1188-115">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="d1188-116">dışı Döndürülen karma değerindeki geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="d1188-116">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="d1188-117">dışı Bir derlemeye uygulanan meta verileri tanımlayan bayrakların işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d1188-117">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="d1188-118">Flags değeri bir veya daha fazla [CorAssemblyFlags](corassemblyflags-enumeration.md) değeri birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="d1188-118">The flags value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1188-119">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d1188-119">Return Value</span></span>  

 <span data-ttu-id="d1188-120">Bu yöntem başarılı olursa S_OK döndürür; Aksi takdirde, Winerror. h üstbilgi dosyasında tanımlanan hata kodlarından birini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d1188-120">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1188-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1188-121">Requirements</span></span>  

 <span data-ttu-id="d1188-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1188-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1188-123">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d1188-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1188-124">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d1188-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1188-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1188-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1188-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1188-126">See also</span></span>

- [<span data-ttu-id="d1188-127">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1188-127">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
