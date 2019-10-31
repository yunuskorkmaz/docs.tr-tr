---
title: StrongNameTokenFromAssembly İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
ms.openlocfilehash: 6b9eca3f2f0267870866874ea27dc65812795f41
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121128"
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="86a99-102">StrongNameTokenFromAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="86a99-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="86a99-103">Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="86a99-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="86a99-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="86a99-104">This function has been deprecated.</span></span> <span data-ttu-id="86a99-105">Bunun yerine [ICLRStrongName:: StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="86a99-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86a99-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86a99-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86a99-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86a99-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="86a99-108">'ndaki Bütünleştirilmiş kod için Taşınabilir çalıştırılabilir (PE) dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="86a99-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="86a99-109">dışı Döndürülen tanımlayıcı ad belirteci.</span><span class="sxs-lookup"><span data-stu-id="86a99-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="86a99-110">dışı Tanımlayıcı ad belirtecinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="86a99-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86a99-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="86a99-111">Return Value</span></span>  
 <span data-ttu-id="86a99-112">başarılı tamamlamada `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="86a99-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86a99-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86a99-113">Remarks</span></span>  
 <span data-ttu-id="86a99-114">Tanımlayıcı ad belirteci, ortak anahtarın kısaltılmış biçimidir.</span><span class="sxs-lookup"><span data-stu-id="86a99-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="86a99-115">Belirteç, derlemeyi imzalamak için kullanılan ortak anahtardan oluşturulan 64 bitlik bir karmadır.</span><span class="sxs-lookup"><span data-stu-id="86a99-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="86a99-116">Belirteç, derlemenin tanımlayıcı adının bir parçasıdır ve derleme meta verilerinden okunabilir.</span><span class="sxs-lookup"><span data-stu-id="86a99-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="86a99-117">Belirteç oluşturulduktan sonra, ayrılan belleği serbest bırakmak için [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="86a99-117">After the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="86a99-118">`StrongNameTokenFromAssembly` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="86a99-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86a99-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86a99-119">Requirements</span></span>  
 <span data-ttu-id="86a99-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86a99-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86a99-121">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="86a99-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="86a99-122">**Kitaplık:** Mscoree. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="86a99-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="86a99-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86a99-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86a99-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86a99-124">See also</span></span>

- [<span data-ttu-id="86a99-125">StrongNameTokenFromAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86a99-125">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="86a99-126">StrongNameTokenFromAssemblyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86a99-126">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="86a99-127">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86a99-127">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
