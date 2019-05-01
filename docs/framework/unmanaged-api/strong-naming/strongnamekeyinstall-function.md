---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b3fc69b2edf611383402b13555cf33be10dbad3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000395"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="661dc-102">StrongNameKeyInstall İşlevi</span><span class="sxs-lookup"><span data-stu-id="661dc-102">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="661dc-103">Bir ortak/özel anahtar çifti bir kapsayıcının içine aktarır.</span><span class="sxs-lookup"><span data-stu-id="661dc-103">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="661dc-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="661dc-104">This function has been deprecated.</span></span> <span data-ttu-id="661dc-105">Kullanım [Iclrstrongname::strongnamekeyınstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="661dc-105">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="661dc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="661dc-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="661dc-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="661dc-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="661dc-108">[in] Anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="661dc-108">[in] The name of the key container.</span></span> <span data-ttu-id="661dc-109">`wszKeyContainer` boş olmayan bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="661dc-109">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="661dc-110">[in] İkili bir anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="661dc-110">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="661dc-111">[in] Bayt cinsinden boyutu, `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="661dc-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="661dc-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="661dc-112">Return Value</span></span>

<span data-ttu-id="661dc-113">`true` başarıyla tamamlandığında; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="661dc-113">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="661dc-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="661dc-114">Remarks</span></span>

<span data-ttu-id="661dc-115">Kullanım [StrongNameKeyDelete](strongnamekeydelete-function.md) işlevi anahtar kapsayıcısı silinemedi.</span><span class="sxs-lookup"><span data-stu-id="661dc-115">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="661dc-116">Varsa `StrongNameKeyInstall` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.</span><span class="sxs-lookup"><span data-stu-id="661dc-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="661dc-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="661dc-117">Requirements</span></span>

<span data-ttu-id="661dc-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="661dc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="661dc-119">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="661dc-119">**Header:** StrongName.h</span></span>

<span data-ttu-id="661dc-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="661dc-120">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="661dc-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="661dc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="661dc-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="661dc-122">See also</span></span>

- [<span data-ttu-id="661dc-123">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="661dc-123">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="661dc-124">StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="661dc-124">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="661dc-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="661dc-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)