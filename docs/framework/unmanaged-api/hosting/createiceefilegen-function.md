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
ms.openlocfilehash: 566f73335861a8eb769b21a254e0e93b51a78d02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151820"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="459ee-102">CreateICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="459ee-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="459ee-103">Oluşturur bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="459ee-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="459ee-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="459ee-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="459ee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="459ee-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="459ee-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="459ee-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="459ee-107">[out] Yeni bir adresini bir işaretçiye `ICeeFileGen` nesne.</span><span class="sxs-lookup"><span data-stu-id="459ee-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="459ee-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="459ee-108">Return Value</span></span>  
 <span data-ttu-id="459ee-109">Bu yöntem standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="459ee-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="459ee-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="459ee-110">Remarks</span></span>  
 <span data-ttu-id="459ee-111">`ICeeFileGen` Nesnesi, ortak dil çalışma zamanı (CLR) taşınabilir çalıştırılabilir (PE) dosyaları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="459ee-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="459ee-112">Çağrı [Destroyıceefilegen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) edilecek işlevi `ICeeFileGen` tamamlandığında nesne.</span><span class="sxs-lookup"><span data-stu-id="459ee-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="459ee-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="459ee-113">Requirements</span></span>  
 <span data-ttu-id="459ee-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="459ee-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="459ee-115">**Üst bilgi:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="459ee-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="459ee-116">**Kitaplığı:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="459ee-116">**Library:** MSCorPE.dll</span></span>  
  
 **<span data-ttu-id="459ee-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="459ee-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="459ee-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="459ee-118">See also</span></span>

- [<span data-ttu-id="459ee-119">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="459ee-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
