---
description: 'Daha fazla bilgi edinin: StrongNameKeyInstall Işlevi'
title: StrongNameKeyInstall İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
ms.openlocfilehash: 0a5d3971ac0927dda7066405adc01a5c80b7faca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670560"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="ff277-103">StrongNameKeyInstall İşlevi</span><span class="sxs-lookup"><span data-stu-id="ff277-103">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="ff277-104">Bir kapsayıcıya ortak/özel anahtar çifti aktarır.</span><span class="sxs-lookup"><span data-stu-id="ff277-104">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="ff277-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ff277-105">This function has been deprecated.</span></span> <span data-ttu-id="ff277-106">Bunun yerine [ICLRStrongName:: StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ff277-106">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="ff277-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff277-107">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="ff277-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff277-108">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="ff277-109">'ndaki Anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="ff277-109">[in] The name of the key container.</span></span> <span data-ttu-id="ff277-110">`wszKeyContainer` boş olmayan bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff277-110">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="ff277-111">'ndaki İkili anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="ff277-111">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="ff277-112">'ndaki Bayt cinsinden boyutu `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="ff277-112">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="ff277-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ff277-113">Return Value</span></span>

<span data-ttu-id="ff277-114">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="ff277-114">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff277-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff277-115">Remarks</span></span>

<span data-ttu-id="ff277-116">Anahtar kapsayıcısını silmek için [StrongNameKeyDelete](strongnamekeydelete-function.md) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ff277-116">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="ff277-117">`StrongNameKeyInstall`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ff277-117">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="ff277-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff277-118">Requirements</span></span>

<span data-ttu-id="ff277-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff277-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ff277-120">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="ff277-120">**Header:** StrongName.h</span></span>

<span data-ttu-id="ff277-121">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ff277-121">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="ff277-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff277-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ff277-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff277-123">See also</span></span>

- [<span data-ttu-id="ff277-124">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff277-124">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="ff277-125">StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff277-125">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="ff277-126">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff277-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
