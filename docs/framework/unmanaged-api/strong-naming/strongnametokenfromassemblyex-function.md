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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95f00fea637b5263699779b7abe9863d266d7f19
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786197"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="075b8-102">StrongNameTokenFromAssemblyEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="075b8-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="075b8-103">Belirtilen derleme dosyasından tanımlayıcı ad belirteci oluşturur ve belirteci temsil eden genel anahtarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="075b8-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="075b8-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="075b8-104">This function has been deprecated.</span></span> <span data-ttu-id="075b8-105">Kullanım [Iclrstrongname::strongnametokenfromassemblyex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="075b8-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="075b8-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="075b8-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="075b8-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="075b8-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="075b8-108">[in] Derleme için taşınabilir yürütülebilir (PE) dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="075b8-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="075b8-109">[out] Döndürülen tanımlayıcı ad belirteç.</span><span class="sxs-lookup"><span data-stu-id="075b8-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="075b8-110">[out] Tanımlayıcı ad belirtecinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="075b8-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="075b8-111">[out] Döndürülen ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="075b8-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="075b8-112">[out] Ortak anahtarın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="075b8-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="075b8-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="075b8-113">Return Value</span></span>  
 <span data-ttu-id="075b8-114">`true` başarıyla tamamlandığında; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="075b8-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="075b8-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="075b8-115">Remarks</span></span>  
 <span data-ttu-id="075b8-116">Genel anahtar kısaltılmış bir tanımlayıcı ad belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="075b8-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="075b8-117">Oluşturulan derlemeyi imzalamak için kullanılacak ortak anahtarı bir 64-bit karma belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="075b8-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="075b8-118">Belirteç, tanımlayıcı ad bütünleştirilmiş kodun bir parçası olan ve derleme meta verileri okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="075b8-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="075b8-119">Anahtar alındığı ve belirteç oluşturulduktan sonra çağırmalısınız [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) ayrılan belleği serbest bırakmak için işlevi.</span><span class="sxs-lookup"><span data-stu-id="075b8-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="075b8-120">Varsa `StrongNameTokenFromAssemblyEx` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.</span><span class="sxs-lookup"><span data-stu-id="075b8-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="075b8-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="075b8-121">Requirements</span></span>  
 <span data-ttu-id="075b8-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="075b8-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="075b8-123">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="075b8-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="075b8-124">**Kitaplığı:** Bir kaynak olarak mscoree.dll dahil</span><span class="sxs-lookup"><span data-stu-id="075b8-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="075b8-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="075b8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="075b8-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="075b8-126">See also</span></span>

- [<span data-ttu-id="075b8-127">StrongNameTokenFromAssemblyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="075b8-127">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="075b8-128">StrongNameTokenFromAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="075b8-128">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="075b8-129">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="075b8-129">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
