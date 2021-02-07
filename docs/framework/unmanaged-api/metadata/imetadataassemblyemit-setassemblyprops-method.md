---
description: ': IMetaDataAssemblyEmit:: SetAssemblyProps Yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataAssemblyEmit::SetAssemblyProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
ms.openlocfilehash: d5dfb5fa472bb83863c8e4909998deeb2b9fc53b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678204"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="56720-103">IMetaDataAssemblyEmit::SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56720-103">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>

<span data-ttu-id="56720-104">Belirtilen `Assembly` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="56720-104">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56720-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56720-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56720-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="56720-106">Parameters</span></span>  

 `pma`  
 <span data-ttu-id="56720-107">'ndaki `Assembly` Değiştirilecek meta veri yapısını belirten meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="56720-107">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="56720-108">'ndaki Derlemenin yayımcısının ortak anahtarına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="56720-108">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="56720-109">'ndaki Bayt cinsinden boyut `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="56720-109">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="56720-110">'ndaki Derleme dosyalarını karma hale yüklemek için kullanılan karma algoritmanın tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="56720-110">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="56720-111">'ndaki Derlemenin insanların okunabilir metin adı.</span><span class="sxs-lookup"><span data-stu-id="56720-111">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="56720-112">'ndaki Derleme için sürüm, platform ve yerel ayar bilgilerini içeren ASSEMBLYMETADATA işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="56720-112">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="56720-113">'ndaki Derlemenin çeşitli özniteliklerini belirten, [AssemblyFlags](assemblyflags-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="56720-113">[in] A bitwise combination of [AssemblyFlags](assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56720-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56720-114">Remarks</span></span>  

 <span data-ttu-id="56720-115">`Assembly`Meta veri yapısı oluşturmak Için [IMetaDataAssemblyEmit::D efineAssembly](imetadataassemblyemit-defineassembly-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="56720-115">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56720-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56720-116">Requirements</span></span>  

 <span data-ttu-id="56720-117">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56720-117">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56720-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="56720-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56720-119">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="56720-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="56720-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56720-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56720-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56720-121">See also</span></span>

- [<span data-ttu-id="56720-122">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56720-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
