---
title: ICLRStrongName::StrongNameKeyDelete Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
ms.openlocfilehash: 4e72818be6808c519677192d3744bbc5ec414d0d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135090"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="670c7-102">ICLRStrongName::StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="670c7-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="670c7-103">Belirtilen anahtar kapsayıcısını siler.</span><span class="sxs-lookup"><span data-stu-id="670c7-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="670c7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="670c7-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="670c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="670c7-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="670c7-106">'ndaki Silinecek anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="670c7-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="670c7-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="670c7-107">Return Value</span></span>  
 <span data-ttu-id="670c7-108">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](https://go.microsoft.com/fwlink/?LinkId=213878) ).</span><span class="sxs-lookup"><span data-stu-id="670c7-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="670c7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="670c7-109">Remarks</span></span>  
 <span data-ttu-id="670c7-110">Bir kapsayıcıya ortak/özel anahtar çifti aktarmak için [ICLRStrongName:: StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="670c7-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="670c7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="670c7-111">Requirements</span></span>  
 <span data-ttu-id="670c7-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="670c7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="670c7-113">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="670c7-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="670c7-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="670c7-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="670c7-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="670c7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="670c7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="670c7-116">See also</span></span>

- [<span data-ttu-id="670c7-117">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="670c7-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="670c7-118">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="670c7-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
