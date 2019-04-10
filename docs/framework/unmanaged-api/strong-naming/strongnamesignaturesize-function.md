---
title: StrongNameSignatureSize İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01c0f9ca0299e817618d93133c0eaca9fc63788e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160322"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="945d8-102">StrongNameSignatureSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="945d8-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="945d8-103">Tanımlayıcı ad imzası boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="945d8-103">Returns the size of the strong name signature.</span></span> `StrongNameSignatureSize` <span data-ttu-id="945d8-104">genellikle derleyiciler tarafından gecikmeli imzalanmış bir derlemeyi oluştururken dosyasında ayırmak için ne kadar alan belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="945d8-104">is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="945d8-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="945d8-105">This function has been deprecated.</span></span> <span data-ttu-id="945d8-106">Kullanım [Iclrstrongname::strongnamesignaturesize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="945d8-106">Use the [ICLRStrongName::StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="945d8-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="945d8-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="945d8-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="945d8-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="945d8-109">[in] Türünden bir yapıyı [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) tanımlayıcı ad imzası oluşturmak için kullanılan anahtar çiftinden ortak kısmını içerir.</span><span class="sxs-lookup"><span data-stu-id="945d8-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="945d8-110">[in] Bayt cinsinden boyutu, `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="945d8-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="945d8-111">[in] Tanımlayıcı ad imzası depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="945d8-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="945d8-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="945d8-112">Return Value</span></span>  
 `true` <span data-ttu-id="945d8-113">başarıyla tamamlandığında; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="945d8-113">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="945d8-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="945d8-114">Remarks</span></span>  
 <span data-ttu-id="945d8-115">Varsa `StrongNameSignatureSize` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.</span><span class="sxs-lookup"><span data-stu-id="945d8-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="945d8-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="945d8-116">Requirements</span></span>  
 <span data-ttu-id="945d8-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="945d8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="945d8-118">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="945d8-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="945d8-119">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="945d8-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="945d8-120">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="945d8-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="945d8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="945d8-121">See also</span></span>

- [<span data-ttu-id="945d8-122">StrongNameSignatureSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="945d8-122">StrongNameSignatureSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="945d8-123">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="945d8-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
