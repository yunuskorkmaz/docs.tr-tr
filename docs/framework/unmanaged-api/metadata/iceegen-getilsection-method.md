---
title: ICeeGen::GetIlSection Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIlSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type:
- apiref
ms.openlocfilehash: c179d5e1ca976d8f425e7c408ceb663cba64f641
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715348"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="ba907-102">ICeeGen::GetIlSection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba907-102">ICeeGen::GetIlSection Method</span></span>

<span data-ttu-id="ba907-103">Belirtilen tanıtıcı tarafından başvurulan ara dil kodu tabanının bölümünü alır.</span><span class="sxs-lookup"><span data-stu-id="ba907-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="ba907-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba907-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba907-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ba907-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba907-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba907-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="ba907-107">'ndaki Alınacak bölüm için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="ba907-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba907-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba907-108">Requirements</span></span>  

 <span data-ttu-id="ba907-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba907-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba907-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ba907-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ba907-111">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ba907-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ba907-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba907-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba907-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba907-113">See also</span></span>

- [<span data-ttu-id="ba907-114">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba907-114">ICeeGen Interface</span></span>](iceegen-interface.md)
