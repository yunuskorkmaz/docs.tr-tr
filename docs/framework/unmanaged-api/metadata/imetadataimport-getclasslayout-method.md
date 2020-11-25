---
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
ms.openlocfilehash: 5a442d8d0916b0e86f25c03507de66fc999f2159
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711266"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="2ff29-102">IMetaDataImport::GetClassLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="2ff29-102">IMetaDataImport::GetClassLayout Method</span></span>

<span data-ttu-id="2ff29-103">Belirtilen TypeDef belirtecinin başvurduğu sınıfa ait düzen bilgisini alır.</span><span class="sxs-lookup"><span data-stu-id="2ff29-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff29-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2ff29-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2ff29-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ff29-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="2ff29-106">'ndaki Döndürülecek düzen ile sınıfın TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="2ff29-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="2ff29-107">dışı Sınıfın paket boyutunu temsil eden 1, 2, 4, 8 veya 16 değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="2ff29-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="2ff29-108">dışı [COR_FIELD_OFFSET](cor-field-offset-structure.md) değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="2ff29-108">[out] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2ff29-109">'ndaki Dizinin en büyük boyutu `rFieldOffset` .</span><span class="sxs-lookup"><span data-stu-id="2ff29-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="2ff29-110">dışı İçinde döndürülen öğelerin sayısı `rFieldOffset` .</span><span class="sxs-lookup"><span data-stu-id="2ff29-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="2ff29-111">dışı Tarafından temsil edilen sınıfın bayt cinsinden boyutu `td` .</span><span class="sxs-lookup"><span data-stu-id="2ff29-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ff29-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ff29-112">Requirements</span></span>  

 <span data-ttu-id="2ff29-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ff29-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ff29-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2ff29-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2ff29-115">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2ff29-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ff29-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ff29-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff29-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ff29-117">See also</span></span>

- [<span data-ttu-id="2ff29-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ff29-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2ff29-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ff29-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
