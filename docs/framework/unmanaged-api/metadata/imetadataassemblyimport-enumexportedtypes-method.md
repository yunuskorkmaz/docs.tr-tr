---
title: IMetaDataAssemblyImport::EnumExportedTypes Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
ms.openlocfilehash: f00fe5bce2f808265add228406dfaa2ccc267545
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176012"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="e36e2-102">IMetaDataAssemblyImport::EnumExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e36e2-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="e36e2-103">Derleme bildiriminde başvurulan dışa aktarılan türleri geçerli meta veri kapsamında günceller.</span><span class="sxs-lookup"><span data-stu-id="e36e2-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e36e2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e36e2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e36e2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e36e2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e36e2-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e36e2-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e36e2-107">`EnumExportedTypes` Yöntem ilk kez çağrıldığında bu null bir değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e36e2-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="e36e2-108">[çıkış] `mdExportedType` Meta veri belirteçlerinin numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="e36e2-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e36e2-109">[içinde] `rExportedTypes` Diziye yerleştirilebilir `mdExportedType` belirteçleri maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="e36e2-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e36e2-110">[çıkış] Yerleştirilen belirteçlerin `mdExportedType` `rExportedTypes`sayısı.</span><span class="sxs-lookup"><span data-stu-id="e36e2-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e36e2-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e36e2-111">Return Value</span></span>  
  
|<span data-ttu-id="e36e2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e36e2-112">HRESULT</span></span>|<span data-ttu-id="e36e2-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e36e2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e36e2-114">`EnumExportedTypes`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e36e2-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e36e2-115">Sayısala rendelemek için hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="e36e2-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="e36e2-116">Bu durumda, `pcTokens` sıfıra ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e36e2-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e36e2-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e36e2-117">Requirements</span></span>  
 <span data-ttu-id="e36e2-118">**Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e36e2-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e36e2-119">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e36e2-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e36e2-120">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e36e2-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e36e2-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e36e2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e36e2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e36e2-122">See also</span></span>

- [<span data-ttu-id="e36e2-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e36e2-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
