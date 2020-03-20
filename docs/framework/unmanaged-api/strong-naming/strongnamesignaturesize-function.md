---
title: StrongNameSignatureSize İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
ms.openlocfilehash: a19d875b8fb81f2af3821e69452f0f0ed591cd22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176896"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="dd7ee-102">StrongNameSignatureSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="dd7ee-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="dd7ee-103">Güçlü ad imzasının boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="dd7ee-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="dd7ee-104">`StrongNameSignatureSize`genellikle derleyiciler tarafından, gecikme imzalı bir derleme oluştururken dosyada ne kadar alan ayırılabildiğini belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd7ee-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="dd7ee-105">Bu işlev amortismana kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="dd7ee-105">This function has been deprecated.</span></span> <span data-ttu-id="dd7ee-106">Bunun yerine [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd7ee-106">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd7ee-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd7ee-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="dd7ee-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dd7ee-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="dd7ee-109">[içinde] Güçlü ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](publickeyblob-structure.md) türünden bir yapı.</span><span class="sxs-lookup"><span data-stu-id="dd7ee-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="dd7ee-110">[içinde] Boyutu, bayt, ve. `pbPublicKeyBlob`</span><span class="sxs-lookup"><span data-stu-id="dd7ee-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="dd7ee-111">[içinde] Güçlü ad imzasını depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="dd7ee-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd7ee-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dd7ee-112">Return Value</span></span>  
 <span data-ttu-id="dd7ee-113">`true`başarılı bir şekilde tamamlandığında; aksi `false`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="dd7ee-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd7ee-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd7ee-114">Remarks</span></span>  
 <span data-ttu-id="dd7ee-115">`StrongNameSignatureSize` İşlev başarıyla tamamlanmamışsa, oluşturulan son hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini arayın.</span><span class="sxs-lookup"><span data-stu-id="dd7ee-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd7ee-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd7ee-116">Requirements</span></span>  
 <span data-ttu-id="dd7ee-117">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd7ee-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd7ee-118">**Üstbilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="dd7ee-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="dd7ee-119">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="dd7ee-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd7ee-120">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd7ee-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd7ee-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd7ee-121">See also</span></span>

- [<span data-ttu-id="dd7ee-122">StrongNameSignatureSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dd7ee-122">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="dd7ee-123">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd7ee-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
