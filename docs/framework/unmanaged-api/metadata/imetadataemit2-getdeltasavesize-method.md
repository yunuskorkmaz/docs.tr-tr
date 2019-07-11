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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0b0a190ce57091434006421e6d8551c78cbe66b8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777174"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="e363a-102">IMetaDataEmit2::GetDeltaSaveSize Metodu</span><span class="sxs-lookup"><span data-stu-id="e363a-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="e363a-103">Geçerli Düzenle ve devam et oturumdan sonuçları meta veri boyutu herhangi bir değişiklik gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="e363a-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e363a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e363a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e363a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e363a-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="e363a-106">[in] Aşağıdakilerden birini [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) istenen duyarlık düzeyini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="e363a-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="e363a-107">.NET Framework 2.0 sürümünde, bu parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="e363a-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="e363a-108">[out] Meta veri boyutunu değiştirme.</span><span class="sxs-lookup"><span data-stu-id="e363a-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e363a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e363a-109">Requirements</span></span>  
 <span data-ttu-id="e363a-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e363a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e363a-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="e363a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e363a-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="e363a-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e363a-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e363a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e363a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e363a-114">See also</span></span>

- [<span data-ttu-id="e363a-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e363a-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="e363a-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e363a-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
