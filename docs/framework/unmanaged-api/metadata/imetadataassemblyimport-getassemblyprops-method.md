---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyImport:: GetAssemblyProps yöntemi'
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
ms.openlocfilehash: 9cd3674dcd640bce27ae5d399d0f7de0c2eeca48
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784151"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="0eb55-103">IMetaDataAssemblyImport::GetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0eb55-103">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>

<span data-ttu-id="0eb55-104">Belirtilen meta veri imzasına sahip derleme için özellik kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="0eb55-104">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eb55-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0eb55-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0eb55-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0eb55-106">Parameters</span></span>  

 `mda`  
 <span data-ttu-id="0eb55-107">[in].</span><span class="sxs-lookup"><span data-stu-id="0eb55-107">[in].</span></span> <span data-ttu-id="0eb55-108">`mdAssembly`Özelliklerinin alınacağı derlemeyi temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="0eb55-108">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="0eb55-109">dışı Ortak anahtara veya meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0eb55-109">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="0eb55-110">dışı Döndürülen ortak anahtardaki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="0eb55-110">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="0eb55-111">dışı Derlemedeki dosyaları karma hale almak için kullanılan algoritmanın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0eb55-111">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="0eb55-112">dışı Derlemenin basit adı.</span><span class="sxs-lookup"><span data-stu-id="0eb55-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="0eb55-113">'ndaki , Öğesinin geniş karakter cinsinden boyutu `szName` .</span><span class="sxs-lookup"><span data-stu-id="0eb55-113">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="0eb55-114">dışı Aslında ' de döndürülen geniş karakter sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="0eb55-114">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="0eb55-115">dışı Derleme meta verilerini içeren bir ASSEMBLYMETADATA yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0eb55-115">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="0eb55-116">dışı Bir derlemeye uygulanan meta verileri tanımlayan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="0eb55-116">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="0eb55-117">Bu değer bir veya daha fazla [CorAssemblyFlags](corassemblyflags-enumeration.md) değerinin birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="0eb55-117">This value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0eb55-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0eb55-118">Requirements</span></span>  

 <span data-ttu-id="0eb55-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0eb55-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eb55-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0eb55-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0eb55-121">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0eb55-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0eb55-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eb55-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb55-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0eb55-123">See also</span></span>

- [<span data-ttu-id="0eb55-124">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0eb55-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
