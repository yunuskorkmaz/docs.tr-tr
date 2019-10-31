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
ms.openlocfilehash: d37f990241ae704abef55d863da0f40a31284837
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141589"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="30b83-102">StrongNameKeyDelete İşlevi</span><span class="sxs-lookup"><span data-stu-id="30b83-102">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="30b83-103">Belirtilen anahtar kapsayıcısını siler.</span><span class="sxs-lookup"><span data-stu-id="30b83-103">Deletes the specified key container.</span></span>

<span data-ttu-id="30b83-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="30b83-104">This function has been deprecated.</span></span> <span data-ttu-id="30b83-105">Bunun yerine [ICLRStrongName:: StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="30b83-105">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="30b83-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30b83-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="30b83-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30b83-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="30b83-108">'ndaki Silinecek anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="30b83-108">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="30b83-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="30b83-109">Return Value</span></span>

<span data-ttu-id="30b83-110">başarılı tamamlamada `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="30b83-110">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="30b83-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30b83-111">Remarks</span></span>

<span data-ttu-id="30b83-112">Ortak/özel anahtar çiftini bir kapsayıcıya içeri aktarmak için [Strongnamekeyinstall](strongnamekeyinstall-function.md) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="30b83-112">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="30b83-113">`StrongNameKeyDelete` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="30b83-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="30b83-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30b83-114">Requirements</span></span>

<span data-ttu-id="30b83-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30b83-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="30b83-116">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="30b83-116">**Header:** StrongName.h</span></span>

<span data-ttu-id="30b83-117">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="30b83-117">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="30b83-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30b83-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="30b83-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30b83-119">See also</span></span>

- [<span data-ttu-id="30b83-120">StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30b83-120">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="30b83-121">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30b83-121">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="30b83-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30b83-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
