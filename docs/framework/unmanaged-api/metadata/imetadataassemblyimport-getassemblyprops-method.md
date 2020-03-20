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
ms.openlocfilehash: dfa900e2184a8c415d75f5702c572b14c4018749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177784"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="65adb-102">IMetaDataAssemblyImport::GetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65adb-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="65adb-103">Belirtilen meta veri imzasıyla derleme için özellik kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="65adb-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65adb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65adb-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="65adb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65adb-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="65adb-106">[içinde].</span><span class="sxs-lookup"><span data-stu-id="65adb-106">[in].</span></span> <span data-ttu-id="65adb-107">Özellikleri `mdAssembly` almak için derlemeyi temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="65adb-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="65adb-108">[çıkış] Ortak anahtarveya meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="65adb-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="65adb-109">[çıkış] Döndürülen ortak anahtardaki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="65adb-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="65adb-110">[çıkış] Derlemedeki dosyaları karmalamak için kullanılan algoritmaya işaretçi.</span><span class="sxs-lookup"><span data-stu-id="65adb-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="65adb-111">[çıkış] Derlemenin basit adı.</span><span class="sxs-lookup"><span data-stu-id="65adb-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="65adb-112">[içinde] Boyutu, geniş chars, `szName`ve .</span><span class="sxs-lookup"><span data-stu-id="65adb-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="65adb-113">[çıkış] Geniş karakter sayısı aslında döndü `szName`.</span><span class="sxs-lookup"><span data-stu-id="65adb-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="65adb-114">[çıkış] Derleme meta verilerini içeren bir ASSEMBLYMETADATA yapısına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="65adb-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="65adb-115">[çıkış] Derlemeye uygulanan meta verileri açıklayan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="65adb-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="65adb-116">Bu değer, bir veya daha fazla [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerinin bir leşimidir.</span><span class="sxs-lookup"><span data-stu-id="65adb-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65adb-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65adb-117">Requirements</span></span>  
 <span data-ttu-id="65adb-118">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65adb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65adb-119">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="65adb-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65adb-120">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="65adb-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="65adb-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65adb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65adb-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65adb-122">See also</span></span>

- [<span data-ttu-id="65adb-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65adb-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
