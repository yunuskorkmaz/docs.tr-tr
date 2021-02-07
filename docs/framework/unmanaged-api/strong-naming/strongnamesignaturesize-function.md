---
description: 'Daha fazla bilgi edinin: Strongnametabeturesize Işlevi'
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
ms.openlocfilehash: b3f22a6a4d5455af4dd17cb75edfd18befed7de3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670534"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="9c828-103">StrongNameSignatureSize İşlevi</span><span class="sxs-lookup"><span data-stu-id="9c828-103">StrongNameSignatureSize Function</span></span>

<span data-ttu-id="9c828-104">Tanımlayıcı ad imzasının boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="9c828-104">Returns the size of the strong name signature.</span></span> <span data-ttu-id="9c828-105">`StrongNameSignatureSize` genellikle derleyiciler tarafından, gecikmeli imzalanmış bir derleme oluştururken dosyada ne kadar alan ayrılacağını tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9c828-105">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="9c828-106">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9c828-106">This function has been deprecated.</span></span> <span data-ttu-id="9c828-107">Bunun yerine [ICLRStrongName:: Strongnametifturesize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c828-107">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c828-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c828-108">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="9c828-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c828-109">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="9c828-110">'ndaki Tanımlayıcı ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](publickeyblob-structure.md) türünde bir yapı.</span><span class="sxs-lookup"><span data-stu-id="9c828-110">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="9c828-111">'ndaki Bayt cinsinden boyutu `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="9c828-111">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="9c828-112">'ndaki Tanımlayıcı ad imzasını depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="9c828-112">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c828-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9c828-113">Return Value</span></span>  

 <span data-ttu-id="9c828-114">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="9c828-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c828-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c828-115">Remarks</span></span>  

 <span data-ttu-id="9c828-116">`StrongNameSignatureSize`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="9c828-116">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c828-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c828-117">Requirements</span></span>  

 <span data-ttu-id="9c828-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c828-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c828-119">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="9c828-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9c828-120">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9c828-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c828-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c828-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c828-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c828-122">See also</span></span>

- [<span data-ttu-id="9c828-123">StrongNameSignatureSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c828-123">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="9c828-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c828-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
