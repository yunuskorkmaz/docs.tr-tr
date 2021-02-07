---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataTables:: GetNextString yöntemi'
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
ms.openlocfilehash: b3c4f94a2659b83c89bef322517465a585b63ddc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688019"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="9f1b8-103">IMetaDataTables::GetNextString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f1b8-103">IMetaDataTables::GetNextString Method</span></span>

<span data-ttu-id="9f1b8-104">Geçerli tablo sütunundaki sonraki dizenin dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="9f1b8-104">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f1b8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f1b8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f1b8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f1b8-106">Parameters</span></span>  

 `ixString`  
 <span data-ttu-id="9f1b8-107">'ndaki Dize tablosu sütunundan dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="9f1b8-107">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="9f1b8-108">dışı Sütundaki sonraki dizenin dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9f1b8-108">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f1b8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f1b8-109">Requirements</span></span>  

 <span data-ttu-id="9f1b8-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f1b8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f1b8-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9f1b8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9f1b8-112">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="9f1b8-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9f1b8-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f1b8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f1b8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f1b8-114">See also</span></span>

- [<span data-ttu-id="9f1b8-115">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f1b8-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="9f1b8-116">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f1b8-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
