---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7be1bd2934fbb2e09a39c3042fa9ae314e89d629
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905612"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="b68f5-102">ICeeGen::AllocateMethodBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b68f5-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="b68f5-103">Bir yöntem için belirtilen boyutta bir arabellek oluşturur ve yöntemin göreli sanal adres alır.</span><span class="sxs-lookup"><span data-stu-id="b68f5-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="b68f5-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b68f5-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b68f5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b68f5-105">Syntax</span></span>  
  
```  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b68f5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b68f5-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="b68f5-107">[in] Oluşturmak için arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="b68f5-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="b68f5-108">[out] Döndürülen arabelleği.</span><span class="sxs-lookup"><span data-stu-id="b68f5-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="b68f5-109">[out] Yöntemin göreli sanal adres.</span><span class="sxs-lookup"><span data-stu-id="b68f5-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b68f5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b68f5-110">Requirements</span></span>  
 <span data-ttu-id="b68f5-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b68f5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b68f5-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b68f5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b68f5-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="b68f5-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b68f5-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b68f5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68f5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b68f5-115">See also</span></span>

- [<span data-ttu-id="b68f5-116">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b68f5-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
