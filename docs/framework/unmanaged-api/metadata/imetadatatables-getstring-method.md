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
ms.openlocfilehash: 8ecaa003084064be1071a85aa726c38d773ec0b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672584"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="7ec97-102">IMetaDataTables::GetString Metodu</span><span class="sxs-lookup"><span data-stu-id="7ec97-102">IMetaDataTables::GetString Method</span></span>

<span data-ttu-id="7ec97-103">Geçerli başvuru kapsamındaki tablo sütunundan belirtilen dizindeki dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="7ec97-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ec97-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7ec97-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ec97-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ec97-105">Parameters</span></span>  

 `ixString`  
 <span data-ttu-id="7ec97-106">'ndaki Sonraki değeri aramaya başlamak için kullanılacak dizin.</span><span class="sxs-lookup"><span data-stu-id="7ec97-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="7ec97-107">dışı Döndürülen dize değerine yönelik işaretçiye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7ec97-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ec97-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ec97-108">Requirements</span></span>  

 <span data-ttu-id="7ec97-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ec97-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ec97-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7ec97-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7ec97-111">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="7ec97-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7ec97-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ec97-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec97-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ec97-113">See also</span></span>

- [<span data-ttu-id="7ec97-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ec97-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="7ec97-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ec97-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
