---
title: "StrongNameSignatureSize İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureSize
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureSize
helpviewer_keywords: StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7944763f1c1379228e715b18b563e7aa776fedac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="38672-102">StrongNameSignatureSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="38672-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="38672-103">Tanımlayıcı ad imzası boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="38672-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="38672-104">`StrongNameSignatureSize`genellikle derleyicileri tarafından gecikmeli imzalanmış bir derleme oluştururken dosyasında ayırmak için ne kadar alan belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38672-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="38672-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="38672-105">This function has been deprecated.</span></span> <span data-ttu-id="38672-106">Kullanım [Iclrstrongname::strongnamesignaturesize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="38672-106">Use the [ICLRStrongName::StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38672-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38672-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="38672-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38672-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="38672-109">[in] Türü yapısını [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) sağlam ad imzası oluşturmak için kullanılan anahtar çifti ortak kısmını içerir.</span><span class="sxs-lookup"><span data-stu-id="38672-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="38672-110">[in] Bayt olarak boyutu, `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="38672-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="38672-111">[in] Tanımlayıcı ad imzası depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="38672-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38672-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="38672-112">Return Value</span></span>  
 <span data-ttu-id="38672-113">`true`başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="38672-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38672-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38672-114">Remarks</span></span>  
 <span data-ttu-id="38672-115">Varsa `StrongNameSignatureSize` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="38672-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38672-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38672-116">Requirements</span></span>  
 <span data-ttu-id="38672-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38672-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38672-118">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="38672-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="38672-119">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="38672-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38672-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38672-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38672-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38672-121">See Also</span></span>  
 [<span data-ttu-id="38672-122">StrongNameSignatureSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="38672-122">StrongNameSignatureSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)  
 [<span data-ttu-id="38672-123">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="38672-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
