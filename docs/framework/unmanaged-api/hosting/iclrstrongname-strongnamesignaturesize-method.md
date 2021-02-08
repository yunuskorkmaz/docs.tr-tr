---
description: ': ICLRStrongName:: Strongnametifturesize yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4c3804eea5b7c6325519b19546f25585af649866
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781863"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="3a1a2-103">ICLRStrongName::StrongNameSignatureSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3a1a2-103">ICLRStrongName::StrongNameSignatureSize Method</span></span>

<span data-ttu-id="3a1a2-104">Tanımlayıcı ad imzasının boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a1a2-104">Returns the size of the strong name signature.</span></span> <span data-ttu-id="3a1a2-105">Bu yöntem genellikle derleyiciler tarafından, gecikmeli imzalanmış bir derleme oluştururken dosyada ne kadar alan ayrılacağını tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a1a2-105">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a1a2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a1a2-106">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="3a1a2-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3a1a2-107">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="3a1a2-108">'ndaki Tanımlayıcı ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) türünde bir yapı.</span><span class="sxs-lookup"><span data-stu-id="3a1a2-108">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="3a1a2-109">'ndaki Bayt cinsinden boyutu `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="3a1a2-109">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="3a1a2-110">'ndaki Tanımlayıcı ad imzasını depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="3a1a2-110">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a1a2-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3a1a2-111">Return Value</span></span>  

 <span data-ttu-id="3a1a2-112">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="3a1a2-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a1a2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3a1a2-113">Requirements</span></span>  

 <span data-ttu-id="3a1a2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a1a2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a1a2-115">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="3a1a2-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3a1a2-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3a1a2-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a1a2-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a1a2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a1a2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a1a2-118">See also</span></span>

- [<span data-ttu-id="3a1a2-119">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3a1a2-119">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
