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
ms.openlocfilehash: 2858e924ab6effe192955ce53dad9d333d2d244d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009073"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="efd73-102">IMetaDataAssemblyImport::GetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efd73-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="efd73-103">Belirtilen meta veri imzasıyla derleme başvurusunun özellik kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="efd73-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efd73-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="efd73-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="efd73-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="efd73-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="efd73-106">'ndaki `mdAssemblyRef`Özelliklerinin alınacağı derleme başvurusunu temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="efd73-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="efd73-107">dışı Ortak anahtara veya meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="efd73-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="efd73-108">dışı Döndürülen ortak anahtar veya belirteçteki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="efd73-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="efd73-109">dışı Derlemenin basit adı.</span><span class="sxs-lookup"><span data-stu-id="efd73-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="efd73-110">'ndaki , Öğesinin geniş karakter cinsinden boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="efd73-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="efd73-111">dışı Aslında ' de döndürülen geniş karakter sayısının bir işaretçisi `szName` .</span><span class="sxs-lookup"><span data-stu-id="efd73-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="efd73-112">dışı Derleme meta verilerini içeren bir ASSEMBLYMETADATA yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="efd73-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="efd73-113">dışı Karma değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="efd73-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="efd73-114">Bu, `PublicKey` [AssemblyRefFlags](assemblyrefflags-enumeration.md) numaralandırması Için arfFullOriginator bayrağı ayarlanmadığı takdirde, başvurulan derlemenin özelliğinin SHA-1 algoritmasını kullanan karmadır.</span><span class="sxs-lookup"><span data-stu-id="efd73-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="efd73-115">dışı Döndürülen karma değerindeki geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="efd73-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="efd73-116">dışı Bir derlemeye uygulanan meta verileri tanımlayan bayrakların işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="efd73-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="efd73-117">Flags değeri bir veya daha fazla [CorAssemblyFlags](corassemblyflags-enumeration.md) değeri birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="efd73-117">The flags value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efd73-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="efd73-118">Return Value</span></span>  
 <span data-ttu-id="efd73-119">Bu yöntem başarılı olursa S_OK döndürür; Aksi takdirde, Winerror. h üstbilgi dosyasında tanımlanan hata kodlarından birini döndürür.</span><span class="sxs-lookup"><span data-stu-id="efd73-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efd73-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="efd73-120">Requirements</span></span>  
 <span data-ttu-id="efd73-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efd73-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efd73-122">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="efd73-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="efd73-123">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="efd73-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="efd73-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efd73-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd73-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efd73-125">See also</span></span>

- [<span data-ttu-id="efd73-126">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="efd73-126">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
