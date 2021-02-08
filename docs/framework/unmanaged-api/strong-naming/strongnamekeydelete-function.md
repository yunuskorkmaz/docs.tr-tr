---
description: 'Daha fazla bilgi edinin: StrongNameKeyDelete Işlevi'
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
ms.openlocfilehash: 9314d961f79e673925125c2362308f9ab4533e75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781213"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="4a7ea-103">StrongNameKeyDelete İşlevi</span><span class="sxs-lookup"><span data-stu-id="4a7ea-103">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="4a7ea-104">Belirtilen anahtar kapsayıcısını siler.</span><span class="sxs-lookup"><span data-stu-id="4a7ea-104">Deletes the specified key container.</span></span>

<span data-ttu-id="4a7ea-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="4a7ea-105">This function has been deprecated.</span></span> <span data-ttu-id="4a7ea-106">Bunun yerine [ICLRStrongName:: StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a7ea-106">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="4a7ea-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a7ea-107">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="4a7ea-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4a7ea-108">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="4a7ea-109">'ndaki Silinecek anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="4a7ea-109">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="4a7ea-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4a7ea-110">Return Value</span></span>

<span data-ttu-id="4a7ea-111">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="4a7ea-111">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a7ea-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a7ea-112">Remarks</span></span>

<span data-ttu-id="4a7ea-113">Ortak/özel anahtar çiftini bir kapsayıcıya içeri aktarmak için [Strongnamekeyinstall](strongnamekeyinstall-function.md) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a7ea-113">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="4a7ea-114">`StrongNameKeyDelete`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="4a7ea-114">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="4a7ea-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a7ea-115">Requirements</span></span>

<span data-ttu-id="4a7ea-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a7ea-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="4a7ea-117">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="4a7ea-117">**Header:** StrongName.h</span></span>

<span data-ttu-id="4a7ea-118">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4a7ea-118">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="4a7ea-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a7ea-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4a7ea-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a7ea-120">See also</span></span>

- [<span data-ttu-id="4a7ea-121">StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a7ea-121">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="4a7ea-122">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a7ea-122">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="4a7ea-123">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a7ea-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
