---
description: ': IMetaDataImport:: GetTypeDefProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: da5c6117f636098ed0cfeddc541979d235729d63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799284"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="a55f6-103">IMetaDataImport::GetTypeDefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a55f6-103">IMetaDataImport::GetTypeDefProps Method</span></span>

<span data-ttu-id="a55f6-104"><xref:System.Type>Belirtilen typedef belirteci tarafından temsil edilen için meta veri bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a55f6-104">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a55f6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a55f6-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a55f6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a55f6-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="a55f6-107">'ndaki Meta verilerini döndürecek türü temsil eden TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="a55f6-107">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="a55f6-108">dışı Tür adını içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="a55f6-108">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="a55f6-109">'ndaki Öğesinin geniş karakterdeki boyutu `szTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="a55f6-109">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="a55f6-110">dışı İçinde döndürülen geniş karakter sayısı `szTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="a55f6-110">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="a55f6-111">dışı Tür tanımını değiştiren bayrakların bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a55f6-111">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="a55f6-112">Bu değer [CorTypeAttr](cortypeattr-enumeration.md) numaralandırmasından bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="a55f6-112">This value is a bitmask from the [CorTypeAttr](cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="a55f6-113">dışı İstenen türün temel türünü temsil eden bir TypeDef veya TypeRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="a55f6-113">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a55f6-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a55f6-114">Requirements</span></span>  

 <span data-ttu-id="a55f6-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a55f6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a55f6-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a55f6-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a55f6-117">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a55f6-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a55f6-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a55f6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a55f6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a55f6-119">See also</span></span>

- [<span data-ttu-id="a55f6-120">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a55f6-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a55f6-121">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a55f6-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
