---
title: ICLRStrongName::StrongNameSignatureSize Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
ms.openlocfilehash: e789996af3aedd17251fc52cde52a336f65053ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176350"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="8ae66-102">ICLRStrongName::StrongNameSignatureSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ae66-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="8ae66-103">Güçlü ad imzasının boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ae66-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="8ae66-104">Bu yöntem genellikle derleyiciler tarafından, gecikme imzalı bir derleme oluştururken dosyada ne kadar alan ayırılabildiğini belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ae66-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ae66-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ae66-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="8ae66-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ae66-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="8ae66-107">[içinde] Güçlü ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) türünden bir yapı.</span><span class="sxs-lookup"><span data-stu-id="8ae66-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="8ae66-108">[içinde] Boyutu, bayt, ve. `pbPublicKeyBlob`</span><span class="sxs-lookup"><span data-stu-id="8ae66-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="8ae66-109">[içinde] Güçlü ad imzasını depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="8ae66-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ae66-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8ae66-110">Return Value</span></span>  
 <span data-ttu-id="8ae66-111">`S_OK`yöntem başarıyla tamamlanırsa; aksi takdirde, başarısızlığı gösteren bir HRESULT değeri (liste için [Ortak HRESULT Değerleri'ne](/windows/win32/seccrypto/common-hresult-values) bakın).</span><span class="sxs-lookup"><span data-stu-id="8ae66-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ae66-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ae66-112">Requirements</span></span>  
 <span data-ttu-id="8ae66-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ae66-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ae66-114">**Üstbilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8ae66-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8ae66-115">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="8ae66-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ae66-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ae66-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ae66-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ae66-117">See also</span></span>

- [<span data-ttu-id="8ae66-118">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ae66-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
