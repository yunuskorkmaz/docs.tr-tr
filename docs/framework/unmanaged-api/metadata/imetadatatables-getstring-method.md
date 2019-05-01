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
ms.openlocfilehash: 8fed98521c0609ebd8b5f65885d69c77814e9e85
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042295"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="ac91c-102">IMetaDataTables::GetString Metodu</span><span class="sxs-lookup"><span data-stu-id="ac91c-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="ac91c-103">Dize, geçerli başvuru kapsamda tablo sütunuyla bağlantısı belirtilen dizindeki alır.</span><span class="sxs-lookup"><span data-stu-id="ac91c-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac91c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac91c-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac91c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac91c-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="ac91c-106">[in] Sonraki değeri aranacağını başlayacağı dizini.</span><span class="sxs-lookup"><span data-stu-id="ac91c-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="ac91c-107">[out] Döndürülen dize değeri için bir işaretçi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ac91c-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac91c-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac91c-108">Requirements</span></span>  
 <span data-ttu-id="ac91c-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac91c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac91c-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ac91c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac91c-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="ac91c-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac91c-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac91c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac91c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac91c-113">See also</span></span>

- [<span data-ttu-id="ac91c-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac91c-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="ac91c-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac91c-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
