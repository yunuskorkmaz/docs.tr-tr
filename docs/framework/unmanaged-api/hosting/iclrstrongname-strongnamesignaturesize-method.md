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
ms.openlocfilehash: 049324baec02fbb03c2db80391ade8a24920a15c
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901089"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="7a253-102">ICLRStrongName::StrongNameSignatureSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a253-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="7a253-103">Tanımlayıcı ad imzasının boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7a253-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="7a253-104">Bu yöntem genellikle derleyiciler tarafından, gecikmeli imzalanmış bir derleme oluştururken dosyada ne kadar alan ayrılacağını tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7a253-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a253-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a253-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="7a253-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a253-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="7a253-107">'ndaki Tanımlayıcı ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) türünde bir yapı.</span><span class="sxs-lookup"><span data-stu-id="7a253-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="7a253-108">'ndaki `pbPublicKeyBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="7a253-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="7a253-109">'ndaki Tanımlayıcı ad imzasını depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7a253-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a253-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7a253-110">Return Value</span></span>  
 <span data-ttu-id="7a253-111">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="7a253-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a253-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a253-112">Requirements</span></span>  
 <span data-ttu-id="7a253-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a253-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a253-114">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="7a253-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7a253-115">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7a253-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a253-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a253-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a253-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a253-117">See also</span></span>

- [<span data-ttu-id="7a253-118">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a253-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
