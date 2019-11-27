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
ms.openlocfilehash: 18fe0c834506d0ac4cd15fd7af4c4f15904b0f81
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437578"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="a2d9f-102">IMetaDataImport::GetEventProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2d9f-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="a2d9f-103">Bildirim türü, temsilciler için ekleme ve kaldırma yöntemleri ve tüm bayraklar ve diğer ilişkili veriler de dahil olmak üzere, belirtilen olay belirteci tarafından temsil edilen olay için meta veri bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="a2d9f-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2d9f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2d9f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a2d9f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2d9f-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="a2d9f-106">'ndaki Meta verilerinin alınacağı olayı temsil eden olay meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="a2d9f-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="a2d9f-107">dışı Olayı bildiren sınıfı temsil eden TypeDef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a2d9f-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="a2d9f-108">dışı `ev`başvurduğu olayın adı.</span><span class="sxs-lookup"><span data-stu-id="a2d9f-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="a2d9f-109">'ndaki `szEvent`geniş karakterdeki istenen uzunluk.</span><span class="sxs-lookup"><span data-stu-id="a2d9f-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="a2d9f-110">dışı `szEvent`geniş karakterde döndürülen uzunluk.</span><span class="sxs-lookup"><span data-stu-id="a2d9f-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="a2d9f-111">dışı Olayın <xref:System.Delegate> türünü temsil eden TypeRef veya TypeDef meta veri belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a2d9f-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="a2d9f-112">dışı Olaya yönelik işleyiciler ekleyen yöntemi temsil eden meta veri belirteci işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a2d9f-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="a2d9f-113">dışı Olay için işleyicileri kaldıran yöntemi temsil eden meta veri belirteci işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a2d9f-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="a2d9f-114">dışı Olayı başlatan yöntemi temsil eden meta veri belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a2d9f-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="a2d9f-115">dışı Olayla ilişkili diğer yöntemlere belirteç işaretçileri dizisi.</span><span class="sxs-lookup"><span data-stu-id="a2d9f-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a2d9f-116">'ndaki `rmdOtherMethod` dizisinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="a2d9f-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="a2d9f-117">dışı `rmdOtherMethod`döndürülen belirteçlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="a2d9f-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2d9f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2d9f-118">Requirements</span></span>  
 <span data-ttu-id="a2d9f-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2d9f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2d9f-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a2d9f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2d9f-121">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a2d9f-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a2d9f-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2d9f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2d9f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2d9f-123">See also</span></span>

- [<span data-ttu-id="a2d9f-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2d9f-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a2d9f-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2d9f-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
