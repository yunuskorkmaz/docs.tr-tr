---
title: IMetaDataTables::GetNextString Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type:
- apiref
ms.openlocfilehash: a1cd932051a9ed90a29ff5eeaa818a67104192bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175258"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="01b0f-102">IMetaDataTables::GetNextString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01b0f-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="01b0f-103">Geçerli tablo sütunundaki sonraki dizenin dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="01b0f-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01b0f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01b0f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01b0f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01b0f-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="01b0f-106">[içinde] Dize tablo sütunundaki dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="01b0f-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="01b0f-107">[çıkış] Sütundaki sonraki dizenin dizinine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="01b0f-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01b0f-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01b0f-108">Requirements</span></span>  
 <span data-ttu-id="01b0f-109">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01b0f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01b0f-110">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="01b0f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01b0f-111">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="01b0f-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="01b0f-112">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01b0f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01b0f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01b0f-113">See also</span></span>

- [<span data-ttu-id="01b0f-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01b0f-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="01b0f-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01b0f-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
