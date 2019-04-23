---
title: ICeeGen::GetString Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 70d78942d4db2fea2cc1ccbcc5ddb20d743e9fdf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093676"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="61ede-102">ICeeGen::GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61ede-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="61ede-103">Belirtilen göreli sanal adresindeki depolanan dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="61ede-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="61ede-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="61ede-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61ede-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61ede-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61ede-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61ede-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="61ede-107">[in] Göreli sanal adres döndürmek için dize.</span><span class="sxs-lookup"><span data-stu-id="61ede-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="61ede-108">[out] Döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="61ede-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61ede-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61ede-109">Requirements</span></span>  
 <span data-ttu-id="61ede-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61ede-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61ede-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="61ede-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61ede-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="61ede-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="61ede-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61ede-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ede-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61ede-114">See also</span></span>

- [<span data-ttu-id="61ede-115">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61ede-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
