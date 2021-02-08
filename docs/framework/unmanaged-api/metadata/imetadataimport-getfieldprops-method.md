---
description: ': IMetaDataImport:: GetFieldProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 76735f837ff53b46b35cdf8c39990ed8689cc69c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789209"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="c7499-103">IMetaDataImport::GetFieldProps Metodu</span><span class="sxs-lookup"><span data-stu-id="c7499-103">IMetaDataImport::GetFieldProps Method</span></span>

<span data-ttu-id="c7499-104">Belirtilen FieldDef belirtecinin başvurduğu alanla ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="c7499-104">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7499-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7499-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c7499-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7499-106">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="c7499-107">'ndaki İlişkili meta verileri almak için alanı temsil eden bir FieldDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="c7499-107">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="c7499-108">dışı Bir TypeDef belirtecinin, alanın ait olduğu sınıfın türünü temsil eden bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c7499-108">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="c7499-109">dışı Alanın adı.</span><span class="sxs-lookup"><span data-stu-id="c7499-109">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="c7499-110">'ndaki *SzField* arabelleğinin geniş karakterdeki boyutu.</span><span class="sxs-lookup"><span data-stu-id="c7499-110">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="c7499-111">dışı Döndürülen arabelleğin gerçek boyutu.</span><span class="sxs-lookup"><span data-stu-id="c7499-111">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="c7499-112">dışı Alanın meta verileriyle ilişkili bayraklar.</span><span class="sxs-lookup"><span data-stu-id="c7499-112">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="c7499-113">'ndaki Alanı açıklayan ikili meta veri değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c7499-113">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="c7499-114">dışı Bayt cinsinden boyut `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="c7499-114">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="c7499-115">dışı Alanın değer türünü belirten bayrak.</span><span class="sxs-lookup"><span data-stu-id="c7499-115">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c7499-116">dışı Alan için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="c7499-116">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="c7499-117">dışı Herhangi bir dize yoksa, karakter cinsinden boyut `ppValue` veya sıfır.</span><span class="sxs-lookup"><span data-stu-id="c7499-117">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7499-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7499-118">Requirements</span></span>  

 <span data-ttu-id="c7499-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7499-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7499-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c7499-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7499-121">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c7499-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7499-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7499-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7499-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7499-123">See also</span></span>

- [<span data-ttu-id="c7499-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7499-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c7499-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7499-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
