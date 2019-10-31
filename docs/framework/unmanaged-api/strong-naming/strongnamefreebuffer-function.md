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
ms.openlocfilehash: 11821acbeeb04ae09464eb0e032b9bf387914168
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095059"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="b53d5-102">StrongNameFreeBuffer İşlevi</span><span class="sxs-lookup"><span data-stu-id="b53d5-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="b53d5-103">[StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)veya [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)gibi bir tanımlayıcı ad işlevine daha önceki bir çağrı ile ayrılmış belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="b53d5-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="b53d5-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="b53d5-104">This function has been deprecated.</span></span> <span data-ttu-id="b53d5-105">Bunun yerine [ICLRStrongName:: StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b53d5-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b53d5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b53d5-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b53d5-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b53d5-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="b53d5-108">'ndaki Boşaltılacak belleğin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b53d5-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b53d5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b53d5-109">Requirements</span></span>  
 <span data-ttu-id="b53d5-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b53d5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b53d5-111">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="b53d5-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b53d5-112">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b53d5-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b53d5-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b53d5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b53d5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b53d5-114">See also</span></span>

- [<span data-ttu-id="b53d5-115">StrongNameFreeBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b53d5-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="b53d5-116">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b53d5-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
