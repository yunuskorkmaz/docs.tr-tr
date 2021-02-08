---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataTables2:: GetMetaDataStorage Yöntemi'
title: IMetaDataTables2::GetMetaDataStorage Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
ms.openlocfilehash: df6bbc69be05986dc6d4f143cec7ec09a2d78ee5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799258"
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="22a98-103">IMetaDataTables2::GetMetaDataStorage Metodu</span><span class="sxs-lookup"><span data-stu-id="22a98-103">IMetaDataTables2::GetMetaDataStorage Method</span></span>

<span data-ttu-id="22a98-104">Belirtilen bölümde depolanan meta verilerin boyutunu ve içeriğini alır.</span><span class="sxs-lookup"><span data-stu-id="22a98-104">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22a98-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22a98-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22a98-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22a98-106">Parameters</span></span>  

 `ppvMd`  
 <span data-ttu-id="22a98-107">[in, out] Meta veri bölümüne yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="22a98-107">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="22a98-108">dışı Meta veri akışının boyutu.</span><span class="sxs-lookup"><span data-stu-id="22a98-108">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22a98-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22a98-109">Requirements</span></span>  

 <span data-ttu-id="22a98-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22a98-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22a98-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="22a98-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22a98-112">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="22a98-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="22a98-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22a98-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a98-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22a98-114">See also</span></span>

- [<span data-ttu-id="22a98-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22a98-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="22a98-116">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22a98-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
