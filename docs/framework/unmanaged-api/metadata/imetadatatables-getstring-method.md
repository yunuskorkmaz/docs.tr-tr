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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ed3501930b94eae59cf38355f8255ecf4165bcc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449588"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="6c37a-102">IMetaDataTables::GetString Metodu</span><span class="sxs-lookup"><span data-stu-id="6c37a-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="6c37a-103">Dize belirtilen dizindeki geçerli başvuru kapsamda tablo sütunuyla bağlantısı alır.</span><span class="sxs-lookup"><span data-stu-id="6c37a-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c37a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c37a-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c37a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c37a-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="6c37a-106">[in] Sonraki değeri aramak üzere başlayacağı dizini.</span><span class="sxs-lookup"><span data-stu-id="6c37a-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="6c37a-107">[out] Döndürülen dize değeri için bir işaretçi bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6c37a-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c37a-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c37a-108">Requirements</span></span>  
 <span data-ttu-id="6c37a-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c37a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c37a-110">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6c37a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c37a-111">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6c37a-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6c37a-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c37a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c37a-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c37a-113">See Also</span></span>  
 [<span data-ttu-id="6c37a-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c37a-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="6c37a-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c37a-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
