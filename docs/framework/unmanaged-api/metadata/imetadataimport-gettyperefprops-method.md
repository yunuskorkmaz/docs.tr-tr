---
description: ': IMetaDataImport:: GetTypeRefProps yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::GetTypeRefProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
ms.openlocfilehash: 8d4741ca2d04aaa4af48fee2cf6485de3403a525
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789131"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="954d5-103">IMetaDataImport::GetTypeRefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="954d5-103">IMetaDataImport::GetTypeRefProps Method</span></span>

<span data-ttu-id="954d5-104">Belirtilen TypeRef belirtecinin başvurduğu ile ilişkili meta verileri alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="954d5-104">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="954d5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="954d5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="954d5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="954d5-106">Parameters</span></span>  

 `tr`  
 <span data-ttu-id="954d5-107">'ndaki Meta verilerini döndürecek türü temsil eden TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="954d5-107">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="954d5-108">dışı Başvurunun yapıldığı kapsama yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="954d5-108">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="954d5-109">Bu değer bir AssemblyRef veya ModuleRef belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="954d5-109">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="954d5-110">dışı Tür adını içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="954d5-110">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="954d5-111">'ndaki Geniş karakterdeki istenen boyut `szName` .</span><span class="sxs-lookup"><span data-stu-id="954d5-111">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="954d5-112">dışı Geniş karakter olarak döndürülen boyut `szName` .</span><span class="sxs-lookup"><span data-stu-id="954d5-112">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="954d5-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="954d5-113">Requirements</span></span>  

 <span data-ttu-id="954d5-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="954d5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="954d5-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="954d5-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="954d5-116">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="954d5-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="954d5-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="954d5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="954d5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="954d5-118">See also</span></span>

- [<span data-ttu-id="954d5-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="954d5-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="954d5-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="954d5-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
