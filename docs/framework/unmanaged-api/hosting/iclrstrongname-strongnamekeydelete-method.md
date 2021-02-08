---
description: ': ICLRStrongName:: StrongNameKeyDelete yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5b782785921eb24394db53d29a66600a3867b489
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799583"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="cb801-103">ICLRStrongName::StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb801-103">ICLRStrongName::StrongNameKeyDelete Method</span></span>

<span data-ttu-id="cb801-104">Belirtilen anahtar kapsayıcısını siler.</span><span class="sxs-lookup"><span data-stu-id="cb801-104">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb801-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb801-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb801-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb801-106">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="cb801-107">'ndaki Silinecek anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="cb801-107">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb801-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cb801-108">Return Value</span></span>  

 <span data-ttu-id="cb801-109">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="cb801-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb801-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb801-110">Remarks</span></span>  

 <span data-ttu-id="cb801-111">Bir kapsayıcıya ortak/özel anahtar çifti aktarmak için [ICLRStrongName:: StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="cb801-111">Use the [ICLRStrongName::StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb801-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb801-112">Requirements</span></span>  

 <span data-ttu-id="cb801-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb801-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb801-114">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="cb801-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cb801-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="cb801-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb801-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb801-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb801-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb801-117">See also</span></span>

- [<span data-ttu-id="cb801-118">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb801-118">StrongNameKeyInstall Method</span></span>](iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="cb801-119">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb801-119">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
