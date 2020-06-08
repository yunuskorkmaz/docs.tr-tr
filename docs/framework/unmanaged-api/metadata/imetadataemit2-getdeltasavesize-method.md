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
ms.openlocfilehash: 24fe8fd65b36e133b767cd07c8602aa1ea7b9dfc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493116"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="2aa3e-102">IMetaDataEmit2::GetDeltaSaveSize Metodu</span><span class="sxs-lookup"><span data-stu-id="2aa3e-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="2aa3e-103">Geçerli Düzenle ve devam et oturumunun sonucu olan meta veri boyutundaki herhangi bir değişikliği gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="2aa3e-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aa3e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2aa3e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2aa3e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2aa3e-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="2aa3e-106">'ndaki [CorSaveSize](corsavesize-enumeration.md) değerlerinden biri, istenen duyarlık düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2aa3e-106">[in] One of the [CorSaveSize](corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="2aa3e-107">.NET Framework sürüm 2,0 için, bu parametre yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="2aa3e-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="2aa3e-108">dışı Meta verilerin boyutundaki değişiklik.</span><span class="sxs-lookup"><span data-stu-id="2aa3e-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2aa3e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2aa3e-109">Requirements</span></span>  
 <span data-ttu-id="2aa3e-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2aa3e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2aa3e-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2aa3e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2aa3e-112">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2aa3e-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2aa3e-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2aa3e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aa3e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2aa3e-114">See also</span></span>

- [<span data-ttu-id="2aa3e-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2aa3e-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="2aa3e-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2aa3e-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
