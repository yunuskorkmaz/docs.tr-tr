---
title: IMetaDataEmit2::GetDeltaSaveSize Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
ms.openlocfilehash: 36021333c1efb61e23c16782d8ad721de62c2643
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674348"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="eb934-102">IMetaDataEmit2::GetDeltaSaveSize Metodu</span><span class="sxs-lookup"><span data-stu-id="eb934-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>

<span data-ttu-id="eb934-103">Geçerli Düzenle ve devam et oturumunun sonucu olan meta veri boyutundaki herhangi bir değişikliği gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="eb934-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb934-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="eb934-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb934-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb934-105">Parameters</span></span>  

 `fSave`  
 <span data-ttu-id="eb934-106">'ndaki [CorSaveSize](corsavesize-enumeration.md) değerlerinden biri, istenen duyarlık düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb934-106">[in] One of the [CorSaveSize](corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="eb934-107">.NET Framework sürüm 2,0 için, bu parametre yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="eb934-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="eb934-108">dışı Meta verilerin boyutundaki değişiklik.</span><span class="sxs-lookup"><span data-stu-id="eb934-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb934-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb934-109">Requirements</span></span>  

 <span data-ttu-id="eb934-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb934-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb934-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="eb934-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eb934-112">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="eb934-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eb934-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb934-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb934-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb934-114">See also</span></span>

- [<span data-ttu-id="eb934-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb934-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="eb934-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb934-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
