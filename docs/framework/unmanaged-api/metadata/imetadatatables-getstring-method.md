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
ms.openlocfilehash: 055499230f500cb7249746e1acbf46b4548d25bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426804"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="f947b-102">IMetaDataTables::GetString Metodu</span><span class="sxs-lookup"><span data-stu-id="f947b-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="f947b-103">Geçerli başvuru kapsamındaki tablo sütunundan belirtilen dizindeki dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="f947b-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f947b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f947b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f947b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f947b-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="f947b-106">'ndaki Sonraki değeri aramaya başlamak için kullanılacak dizin.</span><span class="sxs-lookup"><span data-stu-id="f947b-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="f947b-107">dışı Döndürülen dize değerine yönelik işaretçiye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f947b-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f947b-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f947b-108">Requirements</span></span>  
 <span data-ttu-id="f947b-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f947b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f947b-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f947b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f947b-111">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f947b-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f947b-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f947b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f947b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f947b-113">See also</span></span>

- [<span data-ttu-id="f947b-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f947b-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="f947b-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f947b-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
