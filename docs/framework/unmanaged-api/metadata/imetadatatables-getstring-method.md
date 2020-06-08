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
ms.openlocfilehash: 41e7b8193ce3288d526db8d7d8c289b0a053ee4e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489762"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="13e98-102">IMetaDataTables::GetString Metodu</span><span class="sxs-lookup"><span data-stu-id="13e98-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="13e98-103">Geçerli başvuru kapsamındaki tablo sütunundan belirtilen dizindeki dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="13e98-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13e98-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="13e98-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13e98-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13e98-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="13e98-106">'ndaki Sonraki değeri aramaya başlamak için kullanılacak dizin.</span><span class="sxs-lookup"><span data-stu-id="13e98-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="13e98-107">dışı Döndürülen dize değerine yönelik işaretçiye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="13e98-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13e98-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13e98-108">Requirements</span></span>  
 <span data-ttu-id="13e98-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13e98-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13e98-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="13e98-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13e98-111">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="13e98-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13e98-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13e98-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e98-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13e98-113">See also</span></span>

- [<span data-ttu-id="13e98-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13e98-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="13e98-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13e98-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
