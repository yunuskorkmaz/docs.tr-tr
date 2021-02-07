---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyEmit::D efineManifestResource yöntemi'
title: IMetaDataAssemblyEmit::DefineManifestResource Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
ms.openlocfilehash: 53994f1777cbd2e019f14c0ccae375e6424de509
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678334"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="50935-103">IMetaDataAssemblyEmit::DefineManifestResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50935-103">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>

<span data-ttu-id="50935-104">`ManifestResource`Belirtilen bildirim kaynağı için meta veriler içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="50935-104">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50935-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50935-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,
    [in] mdToken                tkImplementation,
    [in] DWORD                  dwOffset,
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50935-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50935-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="50935-107">'ndaki Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="50935-107">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="50935-108">'ndaki `mdtFile` Kaynak sağlayıcısına eşlenen veya türü bir meta veri belirteci `mdtAssemblyRef` .</span><span class="sxs-lookup"><span data-stu-id="50935-108">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="50935-109">NULL değer, meta verilerin katıştırıldığı dosyanın kaynak sağlayıcısı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="50935-109">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="50935-110">'ndaki Dosyanın içindeki kaynağın başlangıcına olan Aralık.</span><span class="sxs-lookup"><span data-stu-id="50935-110">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="50935-111">Tek başına dosyalardaki kaynaklar için bu her zaman sıfır olur.</span><span class="sxs-lookup"><span data-stu-id="50935-111">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="50935-112">Kaynak bir PE (taşınabilir yürütülebilir) dosyasına katıştırılmışsa, bu, Cor. h üstbilgi dosyasında belirtilen konumda başlayan kaynak BLOBUN bir denklüdür.</span><span class="sxs-lookup"><span data-stu-id="50935-112">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="50935-113">'ndaki Kaynak tanımı için özellik ayarlarını belirten bayrak değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="50935-113">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="50935-114">dışı Döndürülen meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="50935-114">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50935-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50935-115">Remarks</span></span>  

 <span data-ttu-id="50935-116">Her bir `ManifestResource` derleme dosyasında uygulanan her kaynak için bir meta veri yapısı tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="50935-116">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50935-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50935-117">Requirements</span></span>  

 <span data-ttu-id="50935-118">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50935-118">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50935-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="50935-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50935-120">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="50935-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50935-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50935-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50935-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50935-122">See also</span></span>

- [<span data-ttu-id="50935-123">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50935-123">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
