---
title: StrongNameKeyDelete İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfc785a48d0cdf1cf2fdc0245a27b8ef35fd2d81
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364527"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="cad69-102">StrongNameKeyDelete İşlevi</span><span class="sxs-lookup"><span data-stu-id="cad69-102">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="cad69-103">Belirtilen anahtar kapsayıcısında siler.</span><span class="sxs-lookup"><span data-stu-id="cad69-103">Deletes the specified key container.</span></span>

<span data-ttu-id="cad69-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="cad69-104">This function has been deprecated.</span></span> <span data-ttu-id="cad69-105">Kullanım [Iclrstrongname::strongnamekeydelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="cad69-105">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="cad69-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cad69-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="cad69-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cad69-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="cad69-108">[in] Silinecek anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="cad69-108">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="cad69-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cad69-109">Return Value</span></span>

<span data-ttu-id="cad69-110">`true` başarıyla tamamlandığında; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="cad69-110">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="cad69-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cad69-111">Remarks</span></span>

<span data-ttu-id="cad69-112">Kullanım [Strongnamekeyınstall](strongnamekeyinstall-function.md) bir kapsayıcıya bir ortak/özel anahtar çifti alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="cad69-112">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="cad69-113">Varsa `StrongNameKeyDelete` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.</span><span class="sxs-lookup"><span data-stu-id="cad69-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="cad69-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cad69-114">Requirements</span></span>

<span data-ttu-id="cad69-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cad69-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="cad69-116">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="cad69-116">**Header:** StrongName.h</span></span>

<span data-ttu-id="cad69-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cad69-117">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="cad69-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cad69-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cad69-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cad69-119">See also</span></span>

- [<span data-ttu-id="cad69-120">StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cad69-120">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="cad69-121">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cad69-121">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="cad69-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cad69-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)