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
ms.openlocfilehash: 353898b72f41acd0c49a43ff05e54f61b99444c4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798999"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="08187-102">StrongNameKeyInstall İşlevi</span><span class="sxs-lookup"><span data-stu-id="08187-102">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="08187-103">Bir kapsayıcıya ortak/özel anahtar çifti aktarır.</span><span class="sxs-lookup"><span data-stu-id="08187-103">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="08187-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="08187-104">This function has been deprecated.</span></span> <span data-ttu-id="08187-105">Bunun yerine [ICLRStrongName:: StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="08187-105">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="08187-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08187-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="08187-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08187-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="08187-108">'ndaki Anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="08187-108">[in] The name of the key container.</span></span> <span data-ttu-id="08187-109">`wszKeyContainer`boş olmayan bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08187-109">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="08187-110">'ndaki İkili anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="08187-110">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="08187-111">'ndaki Bayt cinsinden boyutu `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="08187-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="08187-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="08187-112">Return Value</span></span>

<span data-ttu-id="08187-113">`true`başarıyla tamamlandığında; Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="08187-113">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="08187-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08187-114">Remarks</span></span>

<span data-ttu-id="08187-115">Anahtar kapsayıcısını silmek için [StrongNameKeyDelete](strongnamekeydelete-function.md) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="08187-115">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="08187-116">İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo işlevini çağırın.](strongnameerrorinfo-function.md) `StrongNameKeyInstall`</span><span class="sxs-lookup"><span data-stu-id="08187-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="08187-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08187-117">Requirements</span></span>

<span data-ttu-id="08187-118">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08187-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="08187-119">**Üst bilgi** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="08187-119">**Header:** StrongName.h</span></span>

<span data-ttu-id="08187-120">**Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="08187-120">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="08187-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08187-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="08187-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08187-122">See also</span></span>

- [<span data-ttu-id="08187-123">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08187-123">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="08187-124">StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08187-124">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="08187-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08187-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
