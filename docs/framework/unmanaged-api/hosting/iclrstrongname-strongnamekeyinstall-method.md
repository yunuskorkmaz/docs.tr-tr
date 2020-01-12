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
ms.openlocfilehash: 2a76377857c3cf1e40a328b9a13fb4834321707e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899564"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="47783-102">ICLRStrongName::StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47783-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="47783-103">Bir kapsayıcıya ortak/özel anahtar çifti aktarır.</span><span class="sxs-lookup"><span data-stu-id="47783-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47783-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47783-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47783-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47783-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="47783-106">'ndaki Anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="47783-106">[in] The name of the key container.</span></span> <span data-ttu-id="47783-107">`wszKeyContainer` boş olmayan bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47783-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="47783-108">'ndaki İkili anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="47783-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="47783-109">'ndaki `pbKeyBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="47783-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47783-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="47783-110">Return Value</span></span>  
 <span data-ttu-id="47783-111">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="47783-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47783-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47783-112">Remarks</span></span>  
 <span data-ttu-id="47783-113">Anahtar kapsayıcısını silmek için [ICLRStrongName:: StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="47783-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47783-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47783-114">Requirements</span></span>  
 <span data-ttu-id="47783-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47783-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47783-116">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="47783-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="47783-117">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="47783-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47783-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47783-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47783-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47783-119">See also</span></span>

- [<span data-ttu-id="47783-120">StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47783-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="47783-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47783-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
