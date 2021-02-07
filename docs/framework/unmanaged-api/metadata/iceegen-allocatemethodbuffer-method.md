---
description: 'Şu konuda daha fazla bilgi edinin: ICeeGen:: AllocateMethodBuffer yöntemi'
title: ICeeGen::AllocateMethodBuffer Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
ms.openlocfilehash: ced5ac8b4fdd89fc41c2c70b68c5b49843a519e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707169"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="4827f-103">ICeeGen::AllocateMethodBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4827f-103">ICeeGen::AllocateMethodBuffer Method</span></span>

<span data-ttu-id="4827f-104">Bir yöntem için belirtilen boyutun bir arabelleğini oluşturur ve yöntemin göreli sanal adresini alır.</span><span class="sxs-lookup"><span data-stu-id="4827f-104">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="4827f-105">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4827f-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4827f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4827f-106">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (
    [in]  ULONG    cchBuffer,
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4827f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4827f-107">Parameters</span></span>  

 `cchBuffer`  
 <span data-ttu-id="4827f-108">'ndaki Oluşturulacak arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="4827f-108">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="4827f-109">dışı Döndürülen arabellek.</span><span class="sxs-lookup"><span data-stu-id="4827f-109">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="4827f-110">dışı Metodun göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="4827f-110">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4827f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4827f-111">Requirements</span></span>  

 <span data-ttu-id="4827f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4827f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4827f-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4827f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4827f-114">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4827f-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4827f-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4827f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4827f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4827f-116">See also</span></span>

- [<span data-ttu-id="4827f-117">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4827f-117">ICeeGen Interface</span></span>](iceegen-interface.md)
