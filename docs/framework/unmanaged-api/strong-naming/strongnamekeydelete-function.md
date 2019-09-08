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
ms.openlocfilehash: 17d35193f69966e02ac5e483924fcb3ee2e06758
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799026"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="5c02e-102">StrongNameKeyDelete İşlevi</span><span class="sxs-lookup"><span data-stu-id="5c02e-102">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="5c02e-103">Belirtilen anahtar kapsayıcısını siler.</span><span class="sxs-lookup"><span data-stu-id="5c02e-103">Deletes the specified key container.</span></span>

<span data-ttu-id="5c02e-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="5c02e-104">This function has been deprecated.</span></span> <span data-ttu-id="5c02e-105">Bunun yerine [ICLRStrongName:: StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="5c02e-105">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="5c02e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c02e-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="5c02e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c02e-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="5c02e-108">'ndaki Silinecek anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="5c02e-108">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="5c02e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5c02e-109">Return Value</span></span>

<span data-ttu-id="5c02e-110">`true`başarıyla tamamlandığında; Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="5c02e-110">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5c02e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c02e-111">Remarks</span></span>

<span data-ttu-id="5c02e-112">Ortak/özel anahtar çiftini bir kapsayıcıya içeri aktarmak için [Strongnamekeyinstall](strongnamekeyinstall-function.md) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5c02e-112">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="5c02e-113">İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo işlevini çağırın.](strongnameerrorinfo-function.md) `StrongNameKeyDelete`</span><span class="sxs-lookup"><span data-stu-id="5c02e-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="5c02e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c02e-114">Requirements</span></span>

<span data-ttu-id="5c02e-115">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c02e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="5c02e-116">**Üst bilgi** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="5c02e-116">**Header:** StrongName.h</span></span>

<span data-ttu-id="5c02e-117">**Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="5c02e-117">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="5c02e-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c02e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5c02e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c02e-119">See also</span></span>

- [<span data-ttu-id="5c02e-120">StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c02e-120">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="5c02e-121">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c02e-121">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="5c02e-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c02e-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
