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
ms.openlocfilehash: edce771b3c36f2c56637aa2a21fe524be0ae12c8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763026"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="3e276-102">ICLRStrongName::StrongNameSignatureSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e276-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="3e276-103">Tanımlayıcı ad imzasının boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e276-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="3e276-104">Bu yöntem genellikle derleyiciler tarafından, gecikmeli imzalanmış bir derleme oluştururken dosyada ne kadar alan ayrılacağını tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e276-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e276-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3e276-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="3e276-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e276-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="3e276-107">'ndaki Tanımlayıcı ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) türünde bir yapı.</span><span class="sxs-lookup"><span data-stu-id="3e276-107">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="3e276-108">'ndaki Bayt cinsinden boyutu `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="3e276-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="3e276-109">'ndaki Tanımlayıcı ad imzasını depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="3e276-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e276-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3e276-110">Return Value</span></span>  
 <span data-ttu-id="3e276-111">`S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="3e276-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e276-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e276-112">Requirements</span></span>  
 <span data-ttu-id="3e276-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e276-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e276-114">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="3e276-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3e276-115">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3e276-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e276-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e276-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e276-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e276-117">See also</span></span>

- [<span data-ttu-id="3e276-118">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e276-118">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
