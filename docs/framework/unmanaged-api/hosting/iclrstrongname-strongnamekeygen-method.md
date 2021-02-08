---
description: ': ICLRStrongName:: StrongNameKeyGen yöntemi hakkında daha fazla bilgi edinin'
title: ICLRStrongName::StrongNameKeyGen Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
ms.openlocfilehash: c445e1f0290d907f7820c0000f602f2668f59103
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799567"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="240af-103">ICLRStrongName::StrongNameKeyGen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="240af-103">ICLRStrongName::StrongNameKeyGen Method</span></span>

<span data-ttu-id="240af-104">Tanımlayıcı ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="240af-104">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="240af-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="240af-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="240af-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="240af-106">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="240af-107">'ndaki İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="240af-107">[in] The requested key container name.</span></span> <span data-ttu-id="240af-108">`wszKeyContainer` geçici bir ad oluşturmak için boş olmayan bir dize ya da null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="240af-108">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="240af-109">'ndaki Anahtarın kaydedilip edilmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="240af-109">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="240af-110">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="240af-110">The following values are supported:</span></span>  
  
- <span data-ttu-id="240af-111">0x00000000- `wszKeyContainer` geçici anahtar kapsayıcısı adı oluşturmak için null olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="240af-111">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="240af-112">0x00000001 ( `SN_LEAVE_KEY` )-anahtarın kayıtlı olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="240af-112">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="240af-113">dışı Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="240af-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="240af-114">dışı Bayt cinsinden boyutu `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="240af-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="240af-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="240af-115">Return Value</span></span>  

 <span data-ttu-id="240af-116">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="240af-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="240af-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="240af-117">Remarks</span></span>  

 <span data-ttu-id="240af-118">[ICLRStrongName:: StrongNameKeyGen](iclrstrongname-strongnamekeygen-method.md) yöntemi 1024 bitlik bir anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="240af-118">The [ICLRStrongName::StrongNameKeyGen](iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="240af-119">Anahtar alındıktan sonra, ayrılan belleği serbest bırakmak için [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) metodunu çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="240af-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="240af-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="240af-120">Requirements</span></span>  

 <span data-ttu-id="240af-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="240af-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="240af-122">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="240af-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="240af-123">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="240af-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="240af-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="240af-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="240af-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="240af-125">See also</span></span>

- [<span data-ttu-id="240af-126">StrongNameKeyGenEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="240af-126">StrongNameKeyGenEx Method</span></span>](iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="240af-127">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="240af-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
