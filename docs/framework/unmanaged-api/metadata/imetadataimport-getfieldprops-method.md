---
title: IMetaDataImport::GetFieldProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
ms.openlocfilehash: 8c3f98a124dbbcae3b0500932a2357ed1757951f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177242"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="c0e19-102">IMetaDataImport::GetFieldProps Metodu</span><span class="sxs-lookup"><span data-stu-id="c0e19-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="c0e19-103">Belirtilen FieldDef belirteci tarafından başvurulan alanla ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="c0e19-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0e19-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0e19-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0e19-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0e19-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="c0e19-106">[içinde] İlişkili meta verileri almak için alanı temsil eden bir FieldDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="c0e19-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="c0e19-107">[çıkış] Alanın ait olduğu sınıfın türünü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="c0e19-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="c0e19-108">[çıkış] Alanın adı.</span><span class="sxs-lookup"><span data-stu-id="c0e19-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="c0e19-109">[içinde] *szField*için arabellek geniş karakterler boyutu.</span><span class="sxs-lookup"><span data-stu-id="c0e19-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="c0e19-110">[çıkış] Döndürülen arabelleğe gerçek boyutu.</span><span class="sxs-lookup"><span data-stu-id="c0e19-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="c0e19-111">[çıkış] Alanın meta verileriyle ilişkili bayraklar.</span><span class="sxs-lookup"><span data-stu-id="c0e19-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="c0e19-112">[içinde] Alanı açıklayan ikili meta veri değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c0e19-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="c0e19-113">[çıkış] `ppvSigBlob`Baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="c0e19-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="c0e19-114">[çıkış] Alanın değer türünü belirten bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="c0e19-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c0e19-115">[çıkış] Alan için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="c0e19-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="c0e19-116">[çıkış] Karakterdeki boyut `ppValue`, veya dize yoksa sıfır.</span><span class="sxs-lookup"><span data-stu-id="c0e19-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0e19-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0e19-117">Requirements</span></span>  
 <span data-ttu-id="c0e19-118">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0e19-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0e19-119">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c0e19-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0e19-120">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="c0e19-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c0e19-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0e19-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e19-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0e19-122">See also</span></span>

- [<span data-ttu-id="c0e19-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0e19-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c0e19-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0e19-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
