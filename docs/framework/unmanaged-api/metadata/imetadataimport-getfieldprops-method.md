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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fc4e8140485902e4677bca0228bc125c64b497f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671869"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="b2651-102">IMetaDataImport::GetFieldProps Metodu</span><span class="sxs-lookup"><span data-stu-id="b2651-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="b2651-103">Belirteç belirtilen fieldDef simgesi tarafından başvurulan alanı ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="b2651-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2651-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2651-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="b2651-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2651-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="b2651-106">[in] İlgili meta verilerini almak için alan temsil eden bir fieldDef simgesi belirteci.</span><span class="sxs-lookup"><span data-stu-id="b2651-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="b2651-107">[out] Alanın ait sınıf türünü temsil eden bir tür tanımı belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b2651-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="b2651-108">[out] Alanın adı.</span><span class="sxs-lookup"><span data-stu-id="b2651-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="b2651-109">[in] Geniş karakterler için arabellek boyutu *szField*.</span><span class="sxs-lookup"><span data-stu-id="b2651-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="b2651-110">[out] Döndürülen arabellek gerçek boyutu.</span><span class="sxs-lookup"><span data-stu-id="b2651-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="b2651-111">[out] Alanın meta verileriyle ilişkili bayraklar.</span><span class="sxs-lookup"><span data-stu-id="b2651-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="b2651-112">[in] Alan açıklayan ikili meta veri değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b2651-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="b2651-113">[out] Bayt cinsinden boyutu `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="b2651-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="b2651-114">[out] Alanın değeri türünü belirten bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="b2651-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b2651-115">[out] Alan için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="b2651-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="b2651-116">[out] Karakter boyutu `ppValue`, veya dize varsa sıfır.</span><span class="sxs-lookup"><span data-stu-id="b2651-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2651-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2651-117">Requirements</span></span>  
 <span data-ttu-id="b2651-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2651-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2651-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b2651-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2651-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b2651-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2651-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2651-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2651-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2651-122">See also</span></span>
- [<span data-ttu-id="b2651-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2651-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b2651-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2651-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
