---
description: 'Daha fazla bilgi edinin: StrongNameTokenFromAssembly Işlevi'
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
ms.openlocfilehash: 3646d441da4885624c15d5e53670a8dd8db45160
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794487"
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="39bc9-103">StrongNameTokenFromAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="39bc9-103">StrongNameTokenFromAssembly Function</span></span>

<span data-ttu-id="39bc9-104">Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39bc9-104">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="39bc9-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="39bc9-105">This function has been deprecated.</span></span> <span data-ttu-id="39bc9-106">Bunun yerine [ICLRStrongName:: StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="39bc9-106">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39bc9-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39bc9-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39bc9-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="39bc9-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="39bc9-109">'ndaki Bütünleştirilmiş kod için Taşınabilir çalıştırılabilir (PE) dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="39bc9-109">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="39bc9-110">dışı Döndürülen tanımlayıcı ad belirteci.</span><span class="sxs-lookup"><span data-stu-id="39bc9-110">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="39bc9-111">dışı Tanımlayıcı ad belirtecinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="39bc9-111">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39bc9-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="39bc9-112">Return Value</span></span>  

 <span data-ttu-id="39bc9-113">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="39bc9-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39bc9-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39bc9-114">Remarks</span></span>  

 <span data-ttu-id="39bc9-115">Tanımlayıcı ad belirteci, ortak anahtarın kısaltılmış biçimidir.</span><span class="sxs-lookup"><span data-stu-id="39bc9-115">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="39bc9-116">Belirteç, derlemeyi imzalamak için kullanılan ortak anahtardan oluşturulan 64 bitlik bir karmadır.</span><span class="sxs-lookup"><span data-stu-id="39bc9-116">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="39bc9-117">Belirteç, derlemenin tanımlayıcı adının bir parçasıdır ve derleme meta verilerinden okunabilir.</span><span class="sxs-lookup"><span data-stu-id="39bc9-117">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="39bc9-118">Belirteç oluşturulduktan sonra, ayrılan belleği serbest bırakmak için [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="39bc9-118">After the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="39bc9-119">`StrongNameTokenFromAssembly`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="39bc9-119">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39bc9-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39bc9-120">Requirements</span></span>  

 <span data-ttu-id="39bc9-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39bc9-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39bc9-122">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="39bc9-122">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="39bc9-123">**Kitaplık:** mscoree.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="39bc9-123">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="39bc9-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39bc9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39bc9-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39bc9-125">See also</span></span>

- [<span data-ttu-id="39bc9-126">StrongNameTokenFromAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39bc9-126">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="39bc9-127">StrongNameTokenFromAssemblyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39bc9-127">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="39bc9-128">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39bc9-128">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
