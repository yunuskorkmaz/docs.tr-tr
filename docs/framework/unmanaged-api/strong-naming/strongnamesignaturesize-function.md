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
ms.openlocfilehash: a8856790b655f071df704879a247169f456ae2f5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130869"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="77ff3-102">StrongNameSignatureSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="77ff3-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="77ff3-103">Tanımlayıcı ad imzasının boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="77ff3-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="77ff3-104">`StrongNameSignatureSize`, bir gecikmeli imzalanmış derleme oluştururken dosyada ne kadar alan ayrılacağını belirlemede genellikle derleyiciler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77ff3-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="77ff3-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="77ff3-105">This function has been deprecated.</span></span> <span data-ttu-id="77ff3-106">Bunun yerine [ICLRStrongName:: Strongnametifturesize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="77ff3-106">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77ff3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77ff3-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="77ff3-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77ff3-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="77ff3-109">'ndaki Tanımlayıcı ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](publickeyblob-structure.md) türünde bir yapı.</span><span class="sxs-lookup"><span data-stu-id="77ff3-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="77ff3-110">'ndaki `pbPublicKeyBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="77ff3-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="77ff3-111">'ndaki Tanımlayıcı ad imzasını depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="77ff3-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77ff3-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="77ff3-112">Return Value</span></span>  
 <span data-ttu-id="77ff3-113">başarılı tamamlamada `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="77ff3-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77ff3-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77ff3-114">Remarks</span></span>  
 <span data-ttu-id="77ff3-115">`StrongNameSignatureSize` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="77ff3-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77ff3-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77ff3-116">Requirements</span></span>  
 <span data-ttu-id="77ff3-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77ff3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77ff3-118">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="77ff3-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="77ff3-119">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="77ff3-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="77ff3-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77ff3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77ff3-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77ff3-121">See also</span></span>

- [<span data-ttu-id="77ff3-122">StrongNameSignatureSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77ff3-122">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="77ff3-123">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77ff3-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
