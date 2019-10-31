---
title: StrongNameTokenFromAssemblyEx İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
ms.openlocfilehash: 8b7866b92be3195b0a767a823a0d7fb1c0aa4918
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104241"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="febb5-102">StrongNameTokenFromAssemblyEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="febb5-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="febb5-103">Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur ve belirtecin temsil ettiği ortak anahtarı döndürür.</span><span class="sxs-lookup"><span data-stu-id="febb5-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="febb5-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="febb5-104">This function has been deprecated.</span></span> <span data-ttu-id="febb5-105">Bunun yerine [ICLRStrongName:: StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="febb5-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="febb5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="febb5-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="febb5-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="febb5-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="febb5-108">'ndaki Bütünleştirilmiş kod için Taşınabilir çalıştırılabilir (PE) dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="febb5-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="febb5-109">dışı Döndürülen tanımlayıcı ad belirteci.</span><span class="sxs-lookup"><span data-stu-id="febb5-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="febb5-110">dışı Tanımlayıcı ad belirtecinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="febb5-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="febb5-111">dışı Döndürülen ortak anahtar.</span><span class="sxs-lookup"><span data-stu-id="febb5-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="febb5-112">dışı Ortak anahtarın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="febb5-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="febb5-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="febb5-113">Return Value</span></span>  
 <span data-ttu-id="febb5-114">başarılı tamamlamada `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="febb5-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="febb5-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="febb5-115">Remarks</span></span>  
 <span data-ttu-id="febb5-116">Tanımlayıcı ad belirteci, ortak anahtarın kısaltılmış biçimidir.</span><span class="sxs-lookup"><span data-stu-id="febb5-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="febb5-117">Belirteç, derlemeyi imzalamak için kullanılan ortak anahtardan oluşturulan 64 bitlik bir karmadır.</span><span class="sxs-lookup"><span data-stu-id="febb5-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="febb5-118">Belirteç, derlemenin tanımlayıcı adının bir parçasıdır ve derleme meta verilerinden okunabilir.</span><span class="sxs-lookup"><span data-stu-id="febb5-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="febb5-119">Anahtar alındıktan ve belirteç oluşturulduktan sonra, ayrılan belleği serbest bırakmak için [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="febb5-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="febb5-120">`StrongNameTokenFromAssemblyEx` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="febb5-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="febb5-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="febb5-121">Requirements</span></span>  
 <span data-ttu-id="febb5-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="febb5-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="febb5-123">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="febb5-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="febb5-124">**Kitaplık:** Mscoree. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="febb5-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="febb5-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="febb5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="febb5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="febb5-126">See also</span></span>

- [<span data-ttu-id="febb5-127">StrongNameTokenFromAssemblyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="febb5-127">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="febb5-128">StrongNameTokenFromAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="febb5-128">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="febb5-129">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="febb5-129">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
