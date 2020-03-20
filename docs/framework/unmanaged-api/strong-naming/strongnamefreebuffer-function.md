---
title: StrongNameFreeBuffer İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
ms.openlocfilehash: 50e3cc6e677de45be9256a2a818ebd6ed7d8b843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176922"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="c6b75-102">StrongNameFreeBuffer İşlevi</span><span class="sxs-lookup"><span data-stu-id="c6b75-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="c6b75-103">[StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)veya [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)gibi güçlü bir ad işlevine önceki bir çağrıyla ayrılan belleği serbest sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6b75-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="c6b75-104">Bu işlev amortismana kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="c6b75-104">This function has been deprecated.</span></span> <span data-ttu-id="c6b75-105">Bunun yerine [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6b75-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6b75-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6b75-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6b75-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6b75-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="c6b75-108">[içinde] Özgür bellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c6b75-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6b75-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6b75-109">Requirements</span></span>  
 <span data-ttu-id="c6b75-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6b75-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6b75-111">**Üstbilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c6b75-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c6b75-112">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="c6b75-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6b75-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6b75-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6b75-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6b75-114">See also</span></span>

- [<span data-ttu-id="c6b75-115">StrongNameFreeBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6b75-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="c6b75-116">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6b75-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
