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
ms.openlocfilehash: 9d14ec33128596a148ca3509a49c8c97fafe82d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723109"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="6dcf3-102">ICeeGen::GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6dcf3-102">ICeeGen::GetString Method</span></span>

<span data-ttu-id="6dcf3-103">Belirtilen göreli sanal adreste depolanan dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="6dcf3-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="6dcf3-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6dcf3-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dcf3-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6dcf3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dcf3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6dcf3-106">Parameters</span></span>  

 `RVA`  
 <span data-ttu-id="6dcf3-107">'ndaki Döndürülecek dizenin göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="6dcf3-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="6dcf3-108">dışı Döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="6dcf3-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dcf3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6dcf3-109">Requirements</span></span>  

 <span data-ttu-id="6dcf3-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dcf3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dcf3-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6dcf3-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6dcf3-112">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6dcf3-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6dcf3-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dcf3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dcf3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6dcf3-114">See also</span></span>

- [<span data-ttu-id="6dcf3-115">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6dcf3-115">ICeeGen Interface</span></span>](iceegen-interface.md)
