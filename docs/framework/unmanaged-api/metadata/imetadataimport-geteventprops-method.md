---
description: ': IMetaDataImport:: GetEventProps Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 2680c48254ce7386a1a070667896aecd3bfac100
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789222"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="de23c-103">IMetaDataImport::GetEventProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="de23c-103">IMetaDataImport::GetEventProps Method</span></span>

<span data-ttu-id="de23c-104">Bildirim türü, temsilciler için ekleme ve kaldırma yöntemleri ve tüm bayraklar ve diğer ilişkili veriler de dahil olmak üzere, belirtilen olay belirteci tarafından temsil edilen olay için meta veri bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="de23c-104">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de23c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de23c-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="de23c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="de23c-106">Parameters</span></span>  

 `ev`  
 <span data-ttu-id="de23c-107">'ndaki Meta verilerinin alınacağı olayı temsil eden olay meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="de23c-107">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="de23c-108">dışı Olayı bildiren sınıfı temsil eden TypeDef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="de23c-108">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="de23c-109">dışı Tarafından başvurulan olayın adı `ev` .</span><span class="sxs-lookup"><span data-stu-id="de23c-109">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="de23c-110">'ndaki Geniş karakterdeki istenen uzunluk `szEvent` .</span><span class="sxs-lookup"><span data-stu-id="de23c-110">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="de23c-111">dışı Geniş karakter olarak döndürülen uzunluk `szEvent` .</span><span class="sxs-lookup"><span data-stu-id="de23c-111">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="de23c-112">dışı Olay türünü temsil eden TypeRef veya TypeDef meta veri belirtecinin işaretçisi <xref:System.Delegate> .</span><span class="sxs-lookup"><span data-stu-id="de23c-112">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="de23c-113">dışı Olaya yönelik işleyiciler ekleyen yöntemi temsil eden meta veri belirteci işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="de23c-113">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="de23c-114">dışı Olay için işleyicileri kaldıran yöntemi temsil eden meta veri belirteci işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="de23c-114">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="de23c-115">dışı Olayı başlatan yöntemi temsil eden meta veri belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="de23c-115">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="de23c-116">dışı Olayla ilişkili diğer yöntemlere belirteç işaretçileri dizisi.</span><span class="sxs-lookup"><span data-stu-id="de23c-116">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="de23c-117">'ndaki Dizinin en büyük boyutu `rmdOtherMethod` .</span><span class="sxs-lookup"><span data-stu-id="de23c-117">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="de23c-118">dışı İçinde döndürülen belirteçlerin sayısı `rmdOtherMethod` .</span><span class="sxs-lookup"><span data-stu-id="de23c-118">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de23c-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="de23c-119">Requirements</span></span>  

 <span data-ttu-id="de23c-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de23c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de23c-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="de23c-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de23c-122">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="de23c-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="de23c-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de23c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de23c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de23c-124">See also</span></span>

- [<span data-ttu-id="de23c-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="de23c-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="de23c-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="de23c-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
