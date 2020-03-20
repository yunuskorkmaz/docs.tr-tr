---
title: IMetaDataTables::GetString Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
ms.openlocfilehash: 216a1f7bd2ff5a596fa7abf7874b5e603d5a9f7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175245"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="aef28-102">IMetaDataTables::GetString Metodu</span><span class="sxs-lookup"><span data-stu-id="aef28-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="aef28-103">Geçerli başvuru kapsamındaki tablo sütunundan belirtilen dizindeki dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="aef28-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aef28-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aef28-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aef28-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aef28-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="aef28-106">[içinde] Bir sonraki değeri aramaya başlamak için hangi dizin.</span><span class="sxs-lookup"><span data-stu-id="aef28-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="aef28-107">[çıkış] Döndürülen dize değeri için bir işaretçi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="aef28-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aef28-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aef28-108">Requirements</span></span>  
 <span data-ttu-id="aef28-109">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aef28-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aef28-110">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aef28-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aef28-111">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="aef28-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aef28-112">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aef28-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef28-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aef28-113">See also</span></span>

- [<span data-ttu-id="aef28-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aef28-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="aef28-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aef28-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
