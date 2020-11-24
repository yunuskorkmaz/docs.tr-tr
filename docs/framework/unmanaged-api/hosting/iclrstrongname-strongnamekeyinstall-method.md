---
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
ms.openlocfilehash: 7e0c689dad0c288e3af3a3d64ee1bba1c44053c1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674534"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="c1686-102">ICLRStrongName::StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1686-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>

<span data-ttu-id="c1686-103">Bir kapsayıcıya ortak/özel anahtar çifti aktarır.</span><span class="sxs-lookup"><span data-stu-id="c1686-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1686-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c1686-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1686-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1686-105">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="c1686-106">'ndaki Anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="c1686-106">[in] The name of the key container.</span></span> <span data-ttu-id="c1686-107">`wszKeyContainer` boş olmayan bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c1686-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="c1686-108">'ndaki İkili anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="c1686-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="c1686-109">'ndaki Bayt cinsinden boyutu `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="c1686-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1686-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c1686-110">Return Value</span></span>  

 <span data-ttu-id="c1686-111">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="c1686-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1686-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1686-112">Remarks</span></span>  

 <span data-ttu-id="c1686-113">Anahtar kapsayıcısını silmek için [ICLRStrongName:: StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1686-113">Use the [ICLRStrongName::StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1686-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1686-114">Requirements</span></span>  

 <span data-ttu-id="c1686-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1686-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1686-116">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c1686-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c1686-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c1686-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1686-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1686-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1686-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1686-119">See also</span></span>

- [<span data-ttu-id="c1686-120">StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1686-120">StrongNameKeyDelete Method</span></span>](iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="c1686-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1686-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
