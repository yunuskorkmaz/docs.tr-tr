---
description: ': IMetaDataTables:: GetNumTables metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1d1e386b1f1eb0f73fbd0df8ddff9cebc5817692
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687850"
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="0b6ae-103">IMetaDataTables::GetNumTables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b6ae-103">IMetaDataTables::GetNumTables Method</span></span>

<span data-ttu-id="0b6ae-104">Geçerli örnek kapsamındaki tablo sayısını alır `IMetaDataTables` .</span><span class="sxs-lookup"><span data-stu-id="0b6ae-104">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b6ae-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b6ae-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b6ae-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b6ae-106">Parameters</span></span>  

 `pcTables`  
 <span data-ttu-id="0b6ae-107">dışı Geçerli örnek kapsamındaki tablo sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0b6ae-107">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b6ae-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b6ae-108">Requirements</span></span>  

 <span data-ttu-id="0b6ae-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b6ae-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b6ae-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0b6ae-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b6ae-111">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0b6ae-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b6ae-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b6ae-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b6ae-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b6ae-113">See also</span></span>

- [<span data-ttu-id="0b6ae-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b6ae-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="0b6ae-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b6ae-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
