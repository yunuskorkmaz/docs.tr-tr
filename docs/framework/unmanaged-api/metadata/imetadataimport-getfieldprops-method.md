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
ms.openlocfilehash: d7f8cccf8d583645982eb37f6afcb553914679ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777760"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="fb661-102">IMetaDataImport::GetFieldProps Metodu</span><span class="sxs-lookup"><span data-stu-id="fb661-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="fb661-103">Belirteç belirtilen fieldDef simgesi tarafından başvurulan alanı ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="fb661-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb661-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb661-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="fb661-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb661-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="fb661-106">[in] İlgili meta verilerini almak için alan temsil eden bir fieldDef simgesi belirteci.</span><span class="sxs-lookup"><span data-stu-id="fb661-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="fb661-107">[out] Alanın ait sınıf türünü temsil eden bir tür tanımı belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fb661-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="fb661-108">[out] Alanın adı.</span><span class="sxs-lookup"><span data-stu-id="fb661-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="fb661-109">[in] Geniş karakterler için arabellek boyutu *szField*.</span><span class="sxs-lookup"><span data-stu-id="fb661-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="fb661-110">[out] Döndürülen arabellek gerçek boyutu.</span><span class="sxs-lookup"><span data-stu-id="fb661-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="fb661-111">[out] Alanın meta verileriyle ilişkili bayraklar.</span><span class="sxs-lookup"><span data-stu-id="fb661-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="fb661-112">[in] Alan açıklayan ikili meta veri değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fb661-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="fb661-113">[out] Bayt cinsinden boyutu `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="fb661-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="fb661-114">[out] Alanın değeri türünü belirten bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="fb661-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="fb661-115">[out] Alan için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="fb661-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="fb661-116">[out] Karakter boyutu `ppValue`, veya dize varsa sıfır.</span><span class="sxs-lookup"><span data-stu-id="fb661-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb661-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb661-117">Requirements</span></span>  
 <span data-ttu-id="fb661-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb661-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb661-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="fb661-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fb661-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fb661-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fb661-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb661-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb661-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb661-122">See also</span></span>

- [<span data-ttu-id="fb661-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb661-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="fb661-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb661-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
