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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38f98b971e430a2c35a4c484f4f9c4bf387c640c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798961"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="ad85a-102">StrongNameSignatureSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="ad85a-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="ad85a-103">Tanımlayıcı ad imzasının boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ad85a-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="ad85a-104">`StrongNameSignatureSize`genellikle derleyiciler tarafından, gecikmeli imzalanmış bir derleme oluştururken dosyada ne kadar alan ayrılacağını tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ad85a-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="ad85a-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ad85a-105">This function has been deprecated.</span></span> <span data-ttu-id="ad85a-106">Bunun yerine [ICLRStrongName:: Strongnametifturesize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ad85a-106">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad85a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad85a-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="ad85a-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad85a-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="ad85a-109">'ndaki Tanımlayıcı ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](publickeyblob-structure.md) türünde bir yapı.</span><span class="sxs-lookup"><span data-stu-id="ad85a-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="ad85a-110">'ndaki Bayt cinsinden boyutu `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ad85a-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="ad85a-111">'ndaki Tanımlayıcı ad imzasını depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="ad85a-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad85a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ad85a-112">Return Value</span></span>  
 <span data-ttu-id="ad85a-113">`true`başarıyla tamamlandığında; Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="ad85a-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad85a-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad85a-114">Remarks</span></span>  
 <span data-ttu-id="ad85a-115">İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo işlevini çağırın.](strongnameerrorinfo-function.md) `StrongNameSignatureSize`</span><span class="sxs-lookup"><span data-stu-id="ad85a-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad85a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad85a-116">Requirements</span></span>  
 <span data-ttu-id="ad85a-117">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad85a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad85a-118">**Üst bilgi** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="ad85a-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ad85a-119">**Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ad85a-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ad85a-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad85a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad85a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad85a-121">See also</span></span>

- [<span data-ttu-id="ad85a-122">StrongNameSignatureSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad85a-122">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="ad85a-123">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad85a-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
