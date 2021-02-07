---
description: ': IMetaDataEmit2:: GetDeltaSaveSize Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d7b5eae7f89a5465876083c5cc8021330d3c59de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745768"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="5535a-103">IMetaDataEmit2::GetDeltaSaveSize Metodu</span><span class="sxs-lookup"><span data-stu-id="5535a-103">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>

<span data-ttu-id="5535a-104">Geçerli Düzenle ve devam et oturumunun sonucu olan meta veri boyutundaki herhangi bir değişikliği gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="5535a-104">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5535a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5535a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5535a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5535a-106">Parameters</span></span>  

 `fSave`  
 <span data-ttu-id="5535a-107">'ndaki [CorSaveSize](corsavesize-enumeration.md) değerlerinden biri, istenen duyarlık düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5535a-107">[in] One of the [CorSaveSize](corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="5535a-108">.NET Framework sürüm 2,0 için, bu parametre yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="5535a-108">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="5535a-109">dışı Meta verilerin boyutundaki değişiklik.</span><span class="sxs-lookup"><span data-stu-id="5535a-109">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5535a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5535a-110">Requirements</span></span>  

 <span data-ttu-id="5535a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5535a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5535a-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5535a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5535a-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5535a-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5535a-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5535a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5535a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5535a-115">See also</span></span>

- [<span data-ttu-id="5535a-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5535a-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="5535a-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5535a-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
