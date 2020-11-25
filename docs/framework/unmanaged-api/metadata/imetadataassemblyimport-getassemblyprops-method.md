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
ms.openlocfilehash: 1e1a86cdf55812197aae653dca256fb910a7f168
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733899"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="aff99-102">IMetaDataAssemblyImport::GetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aff99-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>

<span data-ttu-id="aff99-103">Belirtilen meta veri imzasına sahip derleme için özellik kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="aff99-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aff99-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="aff99-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="aff99-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aff99-105">Parameters</span></span>  

 `mda`  
 <span data-ttu-id="aff99-106">[in].</span><span class="sxs-lookup"><span data-stu-id="aff99-106">[in].</span></span> <span data-ttu-id="aff99-107">`mdAssembly`Özelliklerinin alınacağı derlemeyi temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="aff99-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="aff99-108">dışı Ortak anahtara veya meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="aff99-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="aff99-109">dışı Döndürülen ortak anahtardaki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="aff99-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="aff99-110">dışı Derlemedeki dosyaları karma hale almak için kullanılan algoritmanın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="aff99-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="aff99-111">dışı Derlemenin basit adı.</span><span class="sxs-lookup"><span data-stu-id="aff99-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="aff99-112">'ndaki , Öğesinin geniş karakter cinsinden boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="aff99-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="aff99-113">dışı Aslında ' de döndürülen geniş karakter sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="aff99-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="aff99-114">dışı Derleme meta verilerini içeren bir ASSEMBLYMETADATA yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="aff99-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="aff99-115">dışı Bir derlemeye uygulanan meta verileri tanımlayan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="aff99-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="aff99-116">Bu değer bir veya daha fazla [CorAssemblyFlags](corassemblyflags-enumeration.md) değerinin birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="aff99-116">This value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aff99-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aff99-117">Requirements</span></span>  

 <span data-ttu-id="aff99-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aff99-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aff99-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="aff99-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aff99-120">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="aff99-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aff99-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aff99-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff99-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aff99-122">See also</span></span>

- [<span data-ttu-id="aff99-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aff99-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
