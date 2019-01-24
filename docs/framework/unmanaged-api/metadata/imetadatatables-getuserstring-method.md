---
title: IMetaDataTables::GetUserString Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52f3f382e022600e946a4c8f531f4eea5f3d8a34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693749"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="1198a-102">IMetaDataTables::GetUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="1198a-102">IMetaDataTables::GetUserString Method</span></span>
<span data-ttu-id="1198a-103">Geçerli kapsamdaki dize sütununda belirtilen dizindeki sabit kodlanmış bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="1198a-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1198a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1198a-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
    [in]  ULONG       ixUserString,  
    [out] ULONG       *pcbData,  
    [out] const void  **ppData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1198a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1198a-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="1198a-106">[in] Dizin değeri sabit kodlanmış dize alınır.</span><span class="sxs-lookup"><span data-stu-id="1198a-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="1198a-107">[out] P; boyutuna etçi `ppData`.</span><span class="sxs-lookup"><span data-stu-id="1198a-107">[out] A p;ointer to the size of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="1198a-108">[out] Döndürülen dize için bir işaretçi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1198a-108">[out] A pointer to a pointer to the returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1198a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1198a-109">Requirements</span></span>  
 <span data-ttu-id="1198a-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1198a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1198a-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1198a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1198a-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="1198a-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1198a-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1198a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1198a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1198a-114">See also</span></span>
- [<span data-ttu-id="1198a-115">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1198a-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="1198a-116">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1198a-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
