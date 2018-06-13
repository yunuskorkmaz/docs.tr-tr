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
ms.openlocfilehash: c11de99359701bb6c3198a0b1dc18ba4318c8bc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461207"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="3c3fc-102">StrongNameSignatureSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="3c3fc-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="3c3fc-103">Tanımlayıcı ad imzası boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3c3fc-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="3c3fc-104">`StrongNameSignatureSize` genellikle derleyicileri tarafından gecikmeli imzalanmış bir derleme oluştururken dosyasında ayırmak için ne kadar alan belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c3fc-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="3c3fc-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="3c3fc-105">This function has been deprecated.</span></span> <span data-ttu-id="3c3fc-106">Kullanım [Iclrstrongname::strongnamesignaturesize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="3c3fc-106">Use the [ICLRStrongName::StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c3fc-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c3fc-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c3fc-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c3fc-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="3c3fc-109">[in] Türü yapısını [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) sağlam ad imzası oluşturmak için kullanılan anahtar çifti ortak kısmını içerir.</span><span class="sxs-lookup"><span data-stu-id="3c3fc-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="3c3fc-110">[in] Bayt olarak boyutu, `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="3c3fc-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="3c3fc-111">[in] Tanımlayıcı ad imzası depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="3c3fc-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c3fc-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3c3fc-112">Return Value</span></span>  
 <span data-ttu-id="3c3fc-113">`true` başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="3c3fc-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c3fc-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c3fc-114">Remarks</span></span>  
 <span data-ttu-id="3c3fc-115">Varsa `StrongNameSignatureSize` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="3c3fc-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c3fc-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c3fc-116">Requirements</span></span>  
 <span data-ttu-id="3c3fc-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c3fc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c3fc-118">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="3c3fc-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3c3fc-119">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3c3fc-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3c3fc-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c3fc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c3fc-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c3fc-121">See Also</span></span>  
 [<span data-ttu-id="3c3fc-122">StrongNameSignatureSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c3fc-122">StrongNameSignatureSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)  
 [<span data-ttu-id="3c3fc-123">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c3fc-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
