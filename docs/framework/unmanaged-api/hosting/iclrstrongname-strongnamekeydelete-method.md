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
ms.openlocfilehash: 46345ae570673c9c9c0c58fb6edea1464ba8dd91
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671700"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="7eb98-102">ICLRStrongName::StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7eb98-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>

<span data-ttu-id="7eb98-103">Belirtilen anahtar kapsayıcısını siler.</span><span class="sxs-lookup"><span data-stu-id="7eb98-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eb98-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7eb98-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7eb98-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7eb98-105">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="7eb98-106">'ndaki Silinecek anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="7eb98-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7eb98-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7eb98-107">Return Value</span></span>  

 <span data-ttu-id="7eb98-108">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="7eb98-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7eb98-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7eb98-109">Remarks</span></span>  

 <span data-ttu-id="7eb98-110">Bir kapsayıcıya ortak/özel anahtar çifti aktarmak için [ICLRStrongName:: StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="7eb98-110">Use the [ICLRStrongName::StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eb98-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7eb98-111">Requirements</span></span>  

 <span data-ttu-id="7eb98-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7eb98-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eb98-113">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="7eb98-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7eb98-114">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="7eb98-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7eb98-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eb98-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eb98-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7eb98-116">See also</span></span>

- [<span data-ttu-id="7eb98-117">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7eb98-117">StrongNameKeyInstall Method</span></span>](iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="7eb98-118">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7eb98-118">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
