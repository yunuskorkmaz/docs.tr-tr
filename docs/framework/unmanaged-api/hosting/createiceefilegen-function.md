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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96968de84182b74f7baa89d5dfc12a4797ade595
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779220"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="91c37-102">CreateICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="91c37-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="91c37-103">Oluşturur bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="91c37-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="91c37-104">Bu işlev .NET Framework 4'te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="91c37-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91c37-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91c37-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91c37-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91c37-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="91c37-107">[out] Yeni bir adresini bir işaretçiye `ICeeFileGen` nesne.</span><span class="sxs-lookup"><span data-stu-id="91c37-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91c37-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="91c37-108">Return Value</span></span>  
 <span data-ttu-id="91c37-109">Bu yöntem standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="91c37-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91c37-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91c37-110">Remarks</span></span>  
 <span data-ttu-id="91c37-111">`ICeeFileGen` Nesnesi, ortak dil çalışma zamanı (CLR) taşınabilir çalıştırılabilir (PE) dosyaları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="91c37-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="91c37-112">Çağrı [Destroyıceefilegen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) edilecek işlevi `ICeeFileGen` tamamlandığında nesne.</span><span class="sxs-lookup"><span data-stu-id="91c37-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91c37-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91c37-113">Requirements</span></span>  
 <span data-ttu-id="91c37-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91c37-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91c37-115">**Üst bilgi:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="91c37-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="91c37-116">**Kitaplığı:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="91c37-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="91c37-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91c37-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91c37-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91c37-118">See also</span></span>

- [<span data-ttu-id="91c37-119">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="91c37-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
