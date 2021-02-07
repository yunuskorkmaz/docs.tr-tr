---
description: ': IMetaDataTables:: GetString metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 2104e30657a152d1b9a2ace743da9b126fb15d60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687798"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="97300-103">IMetaDataTables::GetString Metodu</span><span class="sxs-lookup"><span data-stu-id="97300-103">IMetaDataTables::GetString Method</span></span>

<span data-ttu-id="97300-104">Geçerli başvuru kapsamındaki tablo sütunundan belirtilen dizindeki dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="97300-104">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97300-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97300-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97300-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97300-106">Parameters</span></span>  

 `ixString`  
 <span data-ttu-id="97300-107">'ndaki Sonraki değeri aramaya başlamak için kullanılacak dizin.</span><span class="sxs-lookup"><span data-stu-id="97300-107">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="97300-108">dışı Döndürülen dize değerine yönelik işaretçiye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="97300-108">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97300-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97300-109">Requirements</span></span>  

 <span data-ttu-id="97300-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97300-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97300-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="97300-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="97300-112">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="97300-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="97300-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97300-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97300-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97300-114">See also</span></span>

- [<span data-ttu-id="97300-115">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97300-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="97300-116">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97300-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
