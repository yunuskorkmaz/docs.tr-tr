---
description: 'Şu konuda daha fazla bilgi edinin: ICeeGen:: GetString yöntemi'
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
ms.openlocfilehash: 227b4badff3265fc22f1c76301ba03e58fea34c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706909"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="6a8de-103">ICeeGen::GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a8de-103">ICeeGen::GetString Method</span></span>

<span data-ttu-id="6a8de-104">Belirtilen göreli sanal adreste depolanan dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="6a8de-104">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="6a8de-105">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a8de-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a8de-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a8de-106">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a8de-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a8de-107">Parameters</span></span>  

 `RVA`  
 <span data-ttu-id="6a8de-108">'ndaki Döndürülecek dizenin göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="6a8de-108">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="6a8de-109">dışı Döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="6a8de-109">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a8de-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a8de-110">Requirements</span></span>  

 <span data-ttu-id="6a8de-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a8de-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a8de-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6a8de-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a8de-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6a8de-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6a8de-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a8de-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a8de-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a8de-115">See also</span></span>

- [<span data-ttu-id="6a8de-116">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a8de-116">ICeeGen Interface</span></span>](iceegen-interface.md)
