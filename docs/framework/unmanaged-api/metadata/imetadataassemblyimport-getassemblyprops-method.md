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
ms.openlocfilehash: c3c57074ae53e2e1d8d41aa04cb6eb6089db58b5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449437"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="f2df4-102">IMetaDataAssemblyImport::GetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2df4-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="f2df4-103">Belirtilen meta veri imzasına sahip derleme için özellik kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="f2df4-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2df4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2df4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f2df4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2df4-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="f2df4-106">[in].</span><span class="sxs-lookup"><span data-stu-id="f2df4-106">[in].</span></span> <span data-ttu-id="f2df4-107">Özelliklerinin alınacağı derlemeyi temsil eden `mdAssembly` meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="f2df4-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="f2df4-108">dışı Ortak anahtara veya meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f2df4-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="f2df4-109">dışı Döndürülen ortak anahtardaki bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="f2df4-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="f2df4-110">dışı Derlemedeki dosyaları karma hale almak için kullanılan algoritmanın işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f2df4-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="f2df4-111">dışı Derlemenin basit adı.</span><span class="sxs-lookup"><span data-stu-id="f2df4-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f2df4-112">'ndaki `szName`geniş karakter cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="f2df4-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="f2df4-113">dışı `szName`' de döndürülen geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="f2df4-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="f2df4-114">dışı Derleme meta verilerini içeren bir ASSEMBLYMETADATA yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f2df4-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="f2df4-115">dışı Bir derlemeye uygulanan meta verileri tanımlayan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="f2df4-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="f2df4-116">Bu değer bir veya daha fazla [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerinin birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="f2df4-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2df4-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2df4-117">Requirements</span></span>  
 <span data-ttu-id="f2df4-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2df4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2df4-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f2df4-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f2df4-120">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f2df4-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f2df4-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2df4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2df4-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2df4-122">See also</span></span>

- [<span data-ttu-id="f2df4-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2df4-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
