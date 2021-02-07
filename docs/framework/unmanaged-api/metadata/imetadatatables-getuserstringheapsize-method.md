---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataTables:: GetUserStringHeapSize Yöntemi'
title: IMetaDataTables::GetUserStringHeapSize Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
ms.openlocfilehash: 7e6f3eed7803f52e6bde888852c4971900f0868c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687629"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="0f224-103">IMetaDataTables::GetUserStringHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f224-103">IMetaDataTables::GetUserStringHeapSize Method</span></span>

<span data-ttu-id="0f224-104">Kullanıcı dizesi yığınının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="0f224-104">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f224-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f224-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f224-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f224-106">Parameters</span></span>  

 `pcbBlobs`  
 <span data-ttu-id="0f224-107">dışı Kullanıcı dizesi yığınının bayt cinsinden boyutu işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0f224-107">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f224-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f224-108">Requirements</span></span>  

 <span data-ttu-id="0f224-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f224-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f224-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0f224-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0f224-111">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0f224-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0f224-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f224-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f224-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f224-113">See also</span></span>

- [<span data-ttu-id="0f224-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f224-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="0f224-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f224-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
