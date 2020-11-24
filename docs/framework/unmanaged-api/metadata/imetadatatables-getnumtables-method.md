---
title: IMetaDataTables::GetNumTables Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNumTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNumTables
helpviewer_keywords:
- GetNumTables method [.NET Framework metadata]
- IMetaDataTables::GetNumTables method [.NET Framework metadata]
ms.assetid: 8196f2a3-bbf2-45d3-a6cd-74502c356644
topic_type:
- apiref
ms.openlocfilehash: 7e1ea16e7954f21b1349e88d43d7e3b271a57ed7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680301"
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="de3b7-102">IMetaDataTables::GetNumTables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="de3b7-102">IMetaDataTables::GetNumTables Method</span></span>

<span data-ttu-id="de3b7-103">Geçerli örnek kapsamındaki tablo sayısını alır `IMetaDataTables` .</span><span class="sxs-lookup"><span data-stu-id="de3b7-103">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de3b7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="de3b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de3b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="de3b7-105">Parameters</span></span>  

 `pcTables`  
 <span data-ttu-id="de3b7-106">dışı Geçerli örnek kapsamındaki tablo sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="de3b7-106">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de3b7-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="de3b7-107">Requirements</span></span>  

 <span data-ttu-id="de3b7-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de3b7-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de3b7-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="de3b7-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de3b7-110">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="de3b7-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="de3b7-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de3b7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de3b7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de3b7-112">See also</span></span>

- [<span data-ttu-id="de3b7-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="de3b7-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="de3b7-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="de3b7-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
