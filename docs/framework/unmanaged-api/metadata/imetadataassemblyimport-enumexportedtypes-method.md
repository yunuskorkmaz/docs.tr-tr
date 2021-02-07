---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyImport:: Trmexportedtypes yöntemi'
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
ms.openlocfilehash: ecddcbd87586f5f61c57f8c04ea3bd68dc652839
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678035"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="0323f-103">IMetaDataAssemblyImport::EnumExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0323f-103">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>

<span data-ttu-id="0323f-104">Geçerli meta veri kapsamındaki derleme bildiriminde başvurulan verilen türleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="0323f-104">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0323f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0323f-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0323f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0323f-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="0323f-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0323f-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="0323f-108">Yöntem ilk kez çağrıldığında bu null bir değer olmalıdır `EnumExportedTypes` .</span><span class="sxs-lookup"><span data-stu-id="0323f-108">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="0323f-109">dışı `mdExportedType` Meta veri belirteçlerinin numaralandırılması.</span><span class="sxs-lookup"><span data-stu-id="0323f-109">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0323f-110">'ndaki `mdExportedType` Diziye yerleştirilebilecek en fazla belirteç sayısı `rExportedTypes` .</span><span class="sxs-lookup"><span data-stu-id="0323f-110">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0323f-111">dışı `mdExportedType` Gerçekte içine yerleştirilmiş olan belirteçlerin sayısı `rExportedTypes` .</span><span class="sxs-lookup"><span data-stu-id="0323f-111">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0323f-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0323f-112">Return Value</span></span>  
  
|<span data-ttu-id="0323f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0323f-113">HRESULT</span></span>|<span data-ttu-id="0323f-114">Description</span><span class="sxs-lookup"><span data-stu-id="0323f-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0323f-115">`EnumExportedTypes` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0323f-115">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0323f-116">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="0323f-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="0323f-117">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0323f-117">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0323f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0323f-118">Requirements</span></span>  

 <span data-ttu-id="0323f-119">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0323f-119">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0323f-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0323f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0323f-121">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0323f-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0323f-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0323f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0323f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0323f-123">See also</span></span>

- [<span data-ttu-id="0323f-124">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0323f-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
