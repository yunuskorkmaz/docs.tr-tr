---
title: IMetaDataImport::GetTypeDefProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
ms.openlocfilehash: 9dd973fe3e0802c49c220db51a21c223730e5aec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729177"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="7d5cb-102">IMetaDataImport::GetTypeDefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d5cb-102">IMetaDataImport::GetTypeDefProps Method</span></span>

<span data-ttu-id="7d5cb-103"><xref:System.Type>Belirtilen typedef belirteci tarafından temsil edilen için meta veri bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d5cb-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d5cb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7d5cb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d5cb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d5cb-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="7d5cb-106">'ndaki Meta verilerini döndürecek türü temsil eden TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="7d5cb-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="7d5cb-107">dışı Tür adını içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="7d5cb-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="7d5cb-108">'ndaki Öğesinin geniş karakterdeki boyutu `szTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="7d5cb-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="7d5cb-109">dışı İçinde döndürülen geniş karakter sayısı `szTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="7d5cb-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="7d5cb-110">dışı Tür tanımını değiştiren bayrakların bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7d5cb-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="7d5cb-111">Bu değer [CorTypeAttr](cortypeattr-enumeration.md) numaralandırmasından bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="7d5cb-111">This value is a bitmask from the [CorTypeAttr](cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="7d5cb-112">dışı İstenen türün temel türünü temsil eden bir TypeDef veya TypeRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="7d5cb-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d5cb-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d5cb-113">Requirements</span></span>  

 <span data-ttu-id="7d5cb-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d5cb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d5cb-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7d5cb-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7d5cb-116">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="7d5cb-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7d5cb-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d5cb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d5cb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d5cb-118">See also</span></span>

- [<span data-ttu-id="7d5cb-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d5cb-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="7d5cb-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d5cb-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
