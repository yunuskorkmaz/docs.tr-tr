---
description: 'Şu konuda daha fazla bilgi edinin: ICeeGen:: GetMethodBuffer Yöntemi'
title: ICeeGen::GetMethodBuffer Metodu
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
ms.openlocfilehash: 24811f231b1db6d985753d4f4695f432aa12edc2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706948"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="7390c-103">ICeeGen::GetMethodBuffer Metodu</span><span class="sxs-lookup"><span data-stu-id="7390c-103">ICeeGen::GetMethodBuffer Method</span></span>

<span data-ttu-id="7390c-104">Belirtilen göreli sanal adreste Yöntem için uygun boyutun bir arabelleğini alır.</span><span class="sxs-lookup"><span data-stu-id="7390c-104">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="7390c-105">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="7390c-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7390c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7390c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7390c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7390c-107">Parameters</span></span>  

 `RVA`  
 <span data-ttu-id="7390c-108">'ndaki Arabellek döndürülecek yöntemin göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="7390c-108">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="7390c-109">dışı Döndürülen arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7390c-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7390c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7390c-110">Requirements</span></span>  

 <span data-ttu-id="7390c-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7390c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7390c-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7390c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7390c-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="7390c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7390c-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7390c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7390c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7390c-115">See also</span></span>

- [<span data-ttu-id="7390c-116">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7390c-116">ICeeGen Interface</span></span>](iceegen-interface.md)
