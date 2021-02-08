---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataTables2:: Getmetadatastreaınfo yöntemi'
title: IMetaDataTables2::GetMetaDataStreamInfo Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
ms.openlocfilehash: 323c31931cc97f18ff09df83c57153a3629d0a10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799255"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="e10d8-103">IMetaDataTables2::GetMetaDataStreamInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="e10d8-103">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>

<span data-ttu-id="e10d8-104">Belirtilen dizindeki meta veri akışının adını, boyutunu ve içeriğini alır.</span><span class="sxs-lookup"><span data-stu-id="e10d8-104">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e10d8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e10d8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e10d8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e10d8-106">Parameters</span></span>  

 `ix`  
 <span data-ttu-id="e10d8-107">'ndaki İstenen meta veri akışının dizini.</span><span class="sxs-lookup"><span data-stu-id="e10d8-107">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="e10d8-108">dışı Akışın adına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e10d8-108">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="e10d8-109">dışı Meta veri akışına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e10d8-109">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="e10d8-110">dışı Bayt cinsinden boyutu `ppv` .</span><span class="sxs-lookup"><span data-stu-id="e10d8-110">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e10d8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e10d8-111">Requirements</span></span>  

 <span data-ttu-id="e10d8-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e10d8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e10d8-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e10d8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e10d8-114">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e10d8-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e10d8-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e10d8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e10d8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e10d8-116">See also</span></span>

- [<span data-ttu-id="e10d8-117">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e10d8-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="e10d8-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e10d8-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
