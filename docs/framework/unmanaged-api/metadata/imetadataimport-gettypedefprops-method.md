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
ms.openlocfilehash: 6346b1e34e508e5c173bfd0119ac7451d7eef40e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490802"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="c3edb-102">IMetaDataImport::GetTypeDefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3edb-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="c3edb-103"><xref:System.Type>Belirtilen typedef belirteci tarafından temsil edilen için meta veri bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3edb-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3edb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c3edb-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c3edb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3edb-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="c3edb-106">'ndaki Meta verilerini döndürecek türü temsil eden TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="c3edb-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="c3edb-107">dışı Tür adını içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="c3edb-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="c3edb-108">'ndaki Öğesinin geniş karakterdeki boyutu `szTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="c3edb-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="c3edb-109">dışı İçinde döndürülen geniş karakter sayısı `szTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="c3edb-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="c3edb-110">dışı Tür tanımını değiştiren bayrakların bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c3edb-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="c3edb-111">Bu değer [CorTypeAttr](cortypeattr-enumeration.md) numaralandırmasından bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="c3edb-111">This value is a bitmask from the [CorTypeAttr](cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="c3edb-112">dışı İstenen türün temel türünü temsil eden bir TypeDef veya TypeRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="c3edb-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3edb-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3edb-113">Requirements</span></span>  
 <span data-ttu-id="c3edb-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3edb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3edb-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c3edb-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3edb-116">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c3edb-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c3edb-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3edb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3edb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3edb-118">See also</span></span>

- [<span data-ttu-id="c3edb-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3edb-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c3edb-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3edb-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
