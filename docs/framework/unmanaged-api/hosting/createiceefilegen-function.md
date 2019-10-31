---
title: CreateICeeFileGen İşlevi
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
ms.openlocfilehash: de27851b4afc3eccad46531848c68723bff346d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136831"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="05123-102">CreateICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="05123-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="05123-103">Bir [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05123-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="05123-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="05123-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05123-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05123-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05123-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05123-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="05123-107">dışı Yeni bir `ICeeFileGen` nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="05123-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05123-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="05123-108">Return Value</span></span>  
 <span data-ttu-id="05123-109">Bu yöntem, standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="05123-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05123-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05123-110">Remarks</span></span>  
 <span data-ttu-id="05123-111">`ICeeFileGen` nesnesi, ortak dil çalışma zamanı (CLR) taşınabilir yürütülebilir (PE) dosyalarını oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="05123-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="05123-112">`ICeeFileGen` nesnesini tamamlandığında yok etmek için [Destroyııceefilegen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="05123-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05123-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05123-113">Requirements</span></span>  
 <span data-ttu-id="05123-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05123-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05123-115">**Üst bilgi:** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="05123-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="05123-116">**Kitaplık:** MSCorPE. dll</span><span class="sxs-lookup"><span data-stu-id="05123-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="05123-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05123-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05123-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05123-118">See also</span></span>

- [<span data-ttu-id="05123-119">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="05123-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
