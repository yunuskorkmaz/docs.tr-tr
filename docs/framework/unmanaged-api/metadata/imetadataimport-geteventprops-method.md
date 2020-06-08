---
title: IMetaDataImport::GetEventProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
ms.openlocfilehash: 3b47d1559300a462ccda42bc88da43f66c1043ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491309"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="01f31-102">IMetaDataImport::GetEventProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01f31-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="01f31-103">Bildirim türü, temsilciler için ekleme ve kaldırma yöntemleri ve tüm bayraklar ve diğer ilişkili veriler de dahil olmak üzere, belirtilen olay belirteci tarafından temsil edilen olay için meta veri bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="01f31-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f31-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="01f31-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,
   [out] LPCWSTR       szEvent,
   [in]  ULONG         cchEvent,
   [out] ULONG         *pchEvent,
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,
   [out] mdMethodDef   *pmdRemoveOn,
   [out] mdMethodDef   *pmdFire,
   [out] mdMethodDef   rmdOtherMethod[],
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01f31-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01f31-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="01f31-106">'ndaki Meta verilerinin alınacağı olayı temsil eden olay meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="01f31-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="01f31-107">dışı Olayı bildiren sınıfı temsil eden TypeDef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="01f31-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="01f31-108">dışı Tarafından başvurulan olayın adı `ev` .</span><span class="sxs-lookup"><span data-stu-id="01f31-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="01f31-109">'ndaki Geniş karakterdeki istenen uzunluk `szEvent` .</span><span class="sxs-lookup"><span data-stu-id="01f31-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="01f31-110">dışı Geniş karakter olarak döndürülen uzunluk `szEvent` .</span><span class="sxs-lookup"><span data-stu-id="01f31-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="01f31-111">dışı Olay türünü temsil eden TypeRef veya TypeDef meta veri belirtecinin işaretçisi <xref:System.Delegate> .</span><span class="sxs-lookup"><span data-stu-id="01f31-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="01f31-112">dışı Olaya yönelik işleyiciler ekleyen yöntemi temsil eden meta veri belirteci işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="01f31-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="01f31-113">dışı Olay için işleyicileri kaldıran yöntemi temsil eden meta veri belirteci işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="01f31-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="01f31-114">dışı Olayı başlatan yöntemi temsil eden meta veri belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="01f31-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="01f31-115">dışı Olayla ilişkili diğer yöntemlere belirteç işaretçileri dizisi.</span><span class="sxs-lookup"><span data-stu-id="01f31-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="01f31-116">'ndaki Dizinin en büyük boyutu `rmdOtherMethod` .</span><span class="sxs-lookup"><span data-stu-id="01f31-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="01f31-117">dışı İçinde döndürülen belirteçlerin sayısı `rmdOtherMethod` .</span><span class="sxs-lookup"><span data-stu-id="01f31-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01f31-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01f31-118">Requirements</span></span>  
 <span data-ttu-id="01f31-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01f31-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01f31-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="01f31-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01f31-121">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="01f31-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="01f31-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01f31-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f31-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01f31-123">See also</span></span>

- [<span data-ttu-id="01f31-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01f31-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="01f31-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01f31-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
