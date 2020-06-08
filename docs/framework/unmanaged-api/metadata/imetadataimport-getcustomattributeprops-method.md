---
title: IMetaDataImport::GetCustomAttributeProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
ms.openlocfilehash: 320cfae93f8aae94f9315e8e20ed6cf7f9cced7c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491322"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="0beea-102">IMetaDataImport::GetCustomAttributeProps Metodu</span><span class="sxs-lookup"><span data-stu-id="0beea-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="0beea-103">Meta veri belirteci verilen özel özniteliğin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="0beea-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0beea-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0beea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0beea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0beea-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="0beea-106">'ndaki Alınacak özel özniteliği temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="0beea-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="0beea-107">[Out, isteğe bağlı] Özel özniteliğin değiştirdiği nesneyi temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="0beea-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="0beea-108">Bu değer, hariç herhangi bir tür meta veri belirteci olabilir `mdCustomAttribute` .</span><span class="sxs-lookup"><span data-stu-id="0beea-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="0beea-109">[Out, isteğe bağlı] `mdMethodDef` `mdMemberRef` Döndürülen özel özniteliği temsil eden bir veya meta veri belirteci <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="0beea-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="0beea-110">[Out, isteğe bağlı] Özel özniteliğin değeri olan bir veri dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0beea-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="0beea-111">[Out, isteğe bağlı] \* ' De döndürülen verilerin bayt cinsinden boyutu `ppBlob` .</span><span class="sxs-lookup"><span data-stu-id="0beea-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0beea-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0beea-112">Remarks</span></span>  
 <span data-ttu-id="0beea-113">Özel bir öznitelik, veri dizisi olarak, meta veri altyapısı tarafından anlaşılabilecek biçimde depolanır.</span><span class="sxs-lookup"><span data-stu-id="0beea-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0beea-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0beea-114">Requirements</span></span>  
 <span data-ttu-id="0beea-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0beea-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0beea-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0beea-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0beea-117">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0beea-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0beea-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0beea-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0beea-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0beea-119">See also</span></span>

- [<span data-ttu-id="0beea-120">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0beea-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="0beea-121">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0beea-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
