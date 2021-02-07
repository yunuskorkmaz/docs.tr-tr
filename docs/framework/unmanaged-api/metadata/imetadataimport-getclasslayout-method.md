---
description: ': IMetaDataImport:: GetClassLayout metodu hakkında daha fazla bilgi edinin'
title: IMetaDataImport::GetClassLayout Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
ms.openlocfilehash: 74a3170e40a7f857b9150f2d0048af3eac0f2cbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745430"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="f496c-103">IMetaDataImport::GetClassLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="f496c-103">IMetaDataImport::GetClassLayout Method</span></span>

<span data-ttu-id="f496c-104">Belirtilen TypeDef belirtecinin başvurduğu sınıfa ait düzen bilgisini alır.</span><span class="sxs-lookup"><span data-stu-id="f496c-104">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f496c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f496c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f496c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f496c-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="f496c-107">'ndaki Döndürülecek düzen ile sınıfın TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="f496c-107">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="f496c-108">dışı Sınıfın paket boyutunu temsil eden 1, 2, 4, 8 veya 16 değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="f496c-108">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="f496c-109">dışı [COR_FIELD_OFFSET](cor-field-offset-structure.md) değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="f496c-109">[out] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f496c-110">'ndaki Dizinin en büyük boyutu `rFieldOffset` .</span><span class="sxs-lookup"><span data-stu-id="f496c-110">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="f496c-111">dışı İçinde döndürülen öğelerin sayısı `rFieldOffset` .</span><span class="sxs-lookup"><span data-stu-id="f496c-111">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="f496c-112">dışı Tarafından temsil edilen sınıfın bayt cinsinden boyutu `td` .</span><span class="sxs-lookup"><span data-stu-id="f496c-112">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f496c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f496c-113">Requirements</span></span>  

 <span data-ttu-id="f496c-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f496c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f496c-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f496c-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f496c-116">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f496c-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f496c-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f496c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f496c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f496c-118">See also</span></span>

- [<span data-ttu-id="f496c-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f496c-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f496c-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f496c-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
