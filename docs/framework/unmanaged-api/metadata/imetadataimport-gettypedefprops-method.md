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
ms.openlocfilehash: c9ac624e17223def206e86fd92ee4fd2de7f6082
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436755"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="8a513-102">IMetaDataImport::GetTypeDefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a513-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="8a513-103">Belirtilen TypeDef belirteci tarafından temsil edilen <xref:System.Type> için meta veri bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8a513-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a513-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a513-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8a513-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8a513-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="8a513-106">'ndaki Meta verilerini döndürecek türü temsil eden TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="8a513-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="8a513-107">dışı Tür adını içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="8a513-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="8a513-108">'ndaki `szTypeDef`geniş karakterdeki boyut.</span><span class="sxs-lookup"><span data-stu-id="8a513-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="8a513-109">dışı `szTypeDef`' de döndürülen geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="8a513-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="8a513-110">dışı Tür tanımını değiştiren bayrakların bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8a513-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="8a513-111">Bu değer [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) numaralandırmasından bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="8a513-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="8a513-112">dışı İstenen türün temel türünü temsil eden bir TypeDef veya TypeRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="8a513-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a513-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a513-113">Requirements</span></span>  
 <span data-ttu-id="8a513-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a513-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a513-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8a513-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a513-116">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8a513-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a513-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a513-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a513-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a513-118">See also</span></span>

- [<span data-ttu-id="8a513-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a513-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8a513-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a513-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
