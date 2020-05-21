---
title: ICLRStrongName::StrongNameSignatureVerificationFromImage Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
ms.openlocfilehash: 1ba7355fae1888436d57562cc21d3865ebc7a4f4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763182"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="d86df-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d86df-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="d86df-103">Zaten bellekle eşlenmiş bir derlemenin ilişkili ortak anahtar için geçerli olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="d86df-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d86df-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d86df-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d86df-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d86df-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="d86df-106">'ndaki Eşlenen derleme bildiriminin göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="d86df-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="d86df-107">'ndaki Eşlenen görüntünün bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="d86df-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="d86df-108">'ndaki Doğrulama davranışını etkileyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="d86df-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="d86df-109">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d86df-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="d86df-110">`SN_INFLAG_FORCE_VER`(0x00000001)-kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="d86df-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="d86df-111">`SN_INFLAG_INSTALL`(0x00000002)-Bu görüntüde gerçekleştirilen ilk doğrulamanın olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d86df-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="d86df-112">`SN_INFLAG_ADMIN_ACCESS`(0x00000004)-önbelleğin yalnızca yönetici ayrıcalıklarına sahip olan kullanıcılar için erişime izin verolacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d86df-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="d86df-113">`SN_INFLAG_USER_ACCESS`(0x00000008)-derlemenin yalnızca geçerli kullanıcı için erişilebilir olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d86df-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="d86df-114">`SN_INFLAG_ALL_ACCESS`(0x00000010)-önbelleğin erişim kısıtlaması garantisi sunmayacak olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d86df-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="d86df-115">`SN_INFLAG_RUNTIME`(0x80000000)-iç hata ayıklama için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d86df-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="d86df-116">dışı Ek çıkış bilgileri için bayrak.</span><span class="sxs-lookup"><span data-stu-id="d86df-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="d86df-117">Aşağıdaki değer desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d86df-117">The following value is supported:</span></span>  
  
- <span data-ttu-id="d86df-118">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001)-Bu değer `false` , kayıt defteri ayarları nedeniyle doğrulamanın başarılı olduğunu belirtmek için olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d86df-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d86df-119">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d86df-119">Return Value</span></span>  
 <span data-ttu-id="d86df-120">`S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="d86df-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d86df-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d86df-121">Requirements</span></span>  
 <span data-ttu-id="d86df-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d86df-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d86df-123">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d86df-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d86df-124">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d86df-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d86df-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d86df-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d86df-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d86df-126">See also</span></span>

- [<span data-ttu-id="d86df-127">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d86df-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
