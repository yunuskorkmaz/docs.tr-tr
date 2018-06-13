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
ms.openlocfilehash: bc98641085591feaaa5c97c7ee04885ef79d39f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429446"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="1dc4e-102">CreateICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="1dc4e-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="1dc4e-103">Oluşturur bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1dc4e-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="1dc4e-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1dc4e-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dc4e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1dc4e-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1dc4e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1dc4e-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="1dc4e-107">[out] Yeni bir adresini gösteren bir işaretçi `ICeeFileGen` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1dc4e-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dc4e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1dc4e-108">Return Value</span></span>  
 <span data-ttu-id="1dc4e-109">Bu yöntem standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="1dc4e-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1dc4e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1dc4e-110">Remarks</span></span>  
 <span data-ttu-id="1dc4e-111">`ICeeFileGen` Nesnesi ortak dil çalışma zamanı (CLR) taşınabilir yürütülebilir (PE) dosyalarını oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1dc4e-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="1dc4e-112">Çağrı [Destroyıceefilegen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) yok etmek için işlevi `ICeeFileGen` bittiğinde nesne.</span><span class="sxs-lookup"><span data-stu-id="1dc4e-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dc4e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dc4e-113">Requirements</span></span>  
 <span data-ttu-id="1dc4e-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dc4e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dc4e-115">**Başlık:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="1dc4e-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="1dc4e-116">**Kitaplığı:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="1dc4e-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="1dc4e-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dc4e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dc4e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1dc4e-118">See Also</span></span>  
 [<span data-ttu-id="1dc4e-119">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1dc4e-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
