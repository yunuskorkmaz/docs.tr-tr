---
description: ': ICLRStrongName:: StrongNameKeyInstall yöntemi hakkında daha fazla bilgi edinin'
title: ICLRStrongName::StrongNameKeyInstall Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
ms.openlocfilehash: 8f9e7bfebff555a6430a3970c8ee1c481e341f58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799518"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="25c17-103">ICLRStrongName::StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25c17-103">ICLRStrongName::StrongNameKeyInstall Method</span></span>

<span data-ttu-id="25c17-104">Bir kapsayıcıya ortak/özel anahtar çifti aktarır.</span><span class="sxs-lookup"><span data-stu-id="25c17-104">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25c17-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25c17-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25c17-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25c17-106">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="25c17-107">'ndaki Anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="25c17-107">[in] The name of the key container.</span></span> <span data-ttu-id="25c17-108">`wszKeyContainer` boş olmayan bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25c17-108">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="25c17-109">'ndaki İkili anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="25c17-109">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="25c17-110">'ndaki Bayt cinsinden boyutu `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="25c17-110">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25c17-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="25c17-111">Return Value</span></span>  

 <span data-ttu-id="25c17-112">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="25c17-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25c17-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25c17-113">Remarks</span></span>  

 <span data-ttu-id="25c17-114">Anahtar kapsayıcısını silmek için [ICLRStrongName:: StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="25c17-114">Use the [ICLRStrongName::StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25c17-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25c17-115">Requirements</span></span>  

 <span data-ttu-id="25c17-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25c17-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25c17-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="25c17-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="25c17-118">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="25c17-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25c17-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25c17-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25c17-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25c17-120">See also</span></span>

- [<span data-ttu-id="25c17-121">StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25c17-121">StrongNameKeyDelete Method</span></span>](iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="25c17-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25c17-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
