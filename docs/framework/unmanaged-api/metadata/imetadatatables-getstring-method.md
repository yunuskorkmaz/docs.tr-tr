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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119346"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="8e5a3-102">IMetaDataTables::GetString Metodu</span><span class="sxs-lookup"><span data-stu-id="8e5a3-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="8e5a3-103">Dize, geçerli başvuru kapsamda tablo sütunuyla bağlantısı belirtilen dizindeki alır.</span><span class="sxs-lookup"><span data-stu-id="8e5a3-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e5a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e5a3-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e5a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e5a3-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="8e5a3-106">[in] Sonraki değeri aranacağını başlayacağı dizini.</span><span class="sxs-lookup"><span data-stu-id="8e5a3-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="8e5a3-107">[out] Döndürülen dize değeri için bir işaretçi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8e5a3-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e5a3-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e5a3-108">Requirements</span></span>  
 <span data-ttu-id="8e5a3-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e5a3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e5a3-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="8e5a3-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8e5a3-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="8e5a3-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="8e5a3-112">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="8e5a3-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8e5a3-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e5a3-113">See also</span></span>

- [<span data-ttu-id="8e5a3-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e5a3-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="8e5a3-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e5a3-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
