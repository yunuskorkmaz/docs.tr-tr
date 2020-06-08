---
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
ms.openlocfilehash: 273922e00c3e5319d5a03652cc77b69f4479ea67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503529"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="3412c-102">IMetaDataImport::GetTypeRefProps Metodu</span><span class="sxs-lookup"><span data-stu-id="3412c-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="3412c-103">Belirtilen TypeRef belirtecinin başvurduğu ile ilişkili meta verileri alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="3412c-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3412c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3412c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3412c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3412c-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="3412c-106">'ndaki Meta verilerini döndürecek türü temsil eden TypeRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="3412c-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="3412c-107">dışı Başvurunun yapıldığı kapsama yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3412c-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="3412c-108">Bu değer bir AssemblyRef veya ModuleRef belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="3412c-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="3412c-109">dışı Tür adını içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="3412c-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="3412c-110">'ndaki Geniş karakterdeki istenen boyut `szName` .</span><span class="sxs-lookup"><span data-stu-id="3412c-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="3412c-111">dışı Geniş karakter olarak döndürülen boyut `szName` .</span><span class="sxs-lookup"><span data-stu-id="3412c-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3412c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3412c-112">Requirements</span></span>  
 <span data-ttu-id="3412c-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3412c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3412c-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3412c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3412c-115">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3412c-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3412c-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3412c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3412c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3412c-117">See also</span></span>

- [<span data-ttu-id="3412c-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3412c-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3412c-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3412c-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
