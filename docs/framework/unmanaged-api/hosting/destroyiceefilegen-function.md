---
title: DestroyICeeFileGen İşlevi
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
ms.openlocfilehash: 4eb878b61b72378bc6870af7f2cd09f0b6943b13
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136497"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="b0d62-102">DestroyICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="b0d62-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="b0d62-103">Bir [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesnesini yok eder.</span><span class="sxs-lookup"><span data-stu-id="b0d62-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="b0d62-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="b0d62-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0d62-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0d62-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0d62-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0d62-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="b0d62-107">'ndaki Yok edilecek `ICeeFileGen` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b0d62-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0d62-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b0d62-108">Return Value</span></span>  
 <span data-ttu-id="b0d62-109">Bu yöntem, standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b0d62-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0d62-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0d62-110">Remarks</span></span>  
 <span data-ttu-id="b0d62-111">`DestroyICeeFileGen` [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) işlevi tarafından oluşturulan `ICeeFileGen` nesnesini yok eder.</span><span class="sxs-lookup"><span data-stu-id="b0d62-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0d62-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0d62-112">Requirements</span></span>  
 <span data-ttu-id="b0d62-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0d62-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0d62-114">**Üst bilgi:** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="b0d62-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="b0d62-115">**Kitaplık:** MSCorPE. dll</span><span class="sxs-lookup"><span data-stu-id="b0d62-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="b0d62-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0d62-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0d62-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0d62-117">See also</span></span>

- [<span data-ttu-id="b0d62-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b0d62-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
