---
title: IMetaDataAssemblyEmit::DefineExportedType Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 388f227377ddf73fe1297e1c777bb1c0607c13d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177874"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="2df38-102">IMetaDataAssemblyEmit::DefineExportedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2df38-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="2df38-103">Belirtilen dışa aktarılan tür için meta veri içeren bir `ExportedType` yapı oluşturur ve ilişkili meta veri belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="2df38-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2df38-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2df38-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2df38-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2df38-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="2df38-106">[içinde] Dışa aktarılacak türün adı.</span><span class="sxs-lookup"><span data-stu-id="2df38-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="2df38-107">Ortak dil çalışma zamanının sürüm 1.1 sürümü için, dışa aktarılan türün `TypeDef` adı, tür için verilen adla tam olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="2df38-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="2df38-108">[içinde] Dışa aktarılan türün nerede uygulandığını belirten bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="2df38-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="2df38-109">Geçerli değerler ve bunlara bağlı anlamları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2df38-109">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="2df38-110">`mdFile`Tür, bu derleme içinde farklı bir dosyada uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2df38-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="2df38-111">`mdAssemblyRef`Tür farklı bir derlemede uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2df38-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="2df38-112">`mdExportedTYpe`Tür başka bir tür içinde iç içe.</span><span class="sxs-lookup"><span data-stu-id="2df38-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="2df38-113">`mdFileNil`Tür, bildirimle aynı dosyadadır ve iç içe geçen bir tür değildir.</span><span class="sxs-lookup"><span data-stu-id="2df38-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="2df38-114">[içinde] Dışa aktarılacak türü belirten meta verilerin belirteci.</span><span class="sxs-lookup"><span data-stu-id="2df38-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="2df38-115">Bu değer, türü `TypeDef` uygulayan dosyadaki tabloya girilir ve yalnızca bu dosya bu derlemedeyse alakalıdır.</span><span class="sxs-lookup"><span data-stu-id="2df38-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="2df38-116">[içinde] Dışa aktarılan türiçin özellik ayarlarını tanımlayan [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) numaralandırma değerlerinin bitwise kombinasyonu.</span><span class="sxs-lookup"><span data-stu-id="2df38-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="2df38-117">[çıkış] Dışa aktarılan türü gösteren döndürülen meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2df38-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2df38-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2df38-118">Remarks</span></span>  
 <span data-ttu-id="2df38-119">Bu `ExportedType` derleme tarafından maruz kalan ve manifestoyu içeren bir modül dışında bir modülde uygulanan her tür için bir meta veri yapısı tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2df38-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2df38-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2df38-120">Requirements</span></span>  
 <span data-ttu-id="2df38-121">**Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2df38-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2df38-122">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2df38-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2df38-123">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2df38-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2df38-124">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2df38-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df38-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2df38-125">See also</span></span>

- [<span data-ttu-id="2df38-126">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2df38-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
