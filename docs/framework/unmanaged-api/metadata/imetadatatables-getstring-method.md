---
title: IMetaDataTables::GetString Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 687380d3a09a80db216aafbf1ee84c76e31bbf36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="d7aaf-102">IMetaDataTables::GetString Metodu</span><span class="sxs-lookup"><span data-stu-id="d7aaf-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="d7aaf-103">Dize belirtilen dizindeki geçerli başvuru kapsamda tablo sütunuyla bağlantısı alır.</span><span class="sxs-lookup"><span data-stu-id="d7aaf-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7aaf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7aaf-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7aaf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d7aaf-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="d7aaf-106">[in] Sonraki değeri aramak üzere başlayacağı dizini.</span><span class="sxs-lookup"><span data-stu-id="d7aaf-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="d7aaf-107">[out] Döndürülen dize değeri için bir işaretçi bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d7aaf-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7aaf-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7aaf-108">Requirements</span></span>  
 <span data-ttu-id="d7aaf-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7aaf-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7aaf-110">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d7aaf-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d7aaf-111">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d7aaf-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d7aaf-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7aaf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7aaf-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7aaf-113">See Also</span></span>  
 [<span data-ttu-id="d7aaf-114">Imetadatatables arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7aaf-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="d7aaf-115">Imetadatatables2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7aaf-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
