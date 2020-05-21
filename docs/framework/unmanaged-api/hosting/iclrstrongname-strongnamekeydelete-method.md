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
ms.openlocfilehash: 8f6f2445d88d608d51be4e6fe1e064efbb58325d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763104"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="4f987-102">ICLRStrongName::StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f987-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="4f987-103">Belirtilen anahtar kapsayıcısını siler.</span><span class="sxs-lookup"><span data-stu-id="4f987-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f987-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4f987-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f987-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f987-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="4f987-106">'ndaki Silinecek anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="4f987-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f987-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4f987-107">Return Value</span></span>  
 <span data-ttu-id="4f987-108">`S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="4f987-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f987-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f987-109">Remarks</span></span>  
 <span data-ttu-id="4f987-110">Bir kapsayıcıya ortak/özel anahtar çifti aktarmak için [ICLRStrongName:: StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="4f987-110">Use the [ICLRStrongName::StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f987-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f987-111">Requirements</span></span>  
 <span data-ttu-id="4f987-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f987-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f987-113">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="4f987-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4f987-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="4f987-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f987-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f987-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f987-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f987-116">See also</span></span>

- [<span data-ttu-id="4f987-117">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f987-117">StrongNameKeyInstall Method</span></span>](iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="4f987-118">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f987-118">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
