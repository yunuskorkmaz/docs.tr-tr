---
title: ICLRStrongName::StrongNameTokenFromAssemblyEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
ms.openlocfilehash: f08006c532d2778de67a4bab09623d248362535c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937437"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="99a5e-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99a5e-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>
<span data-ttu-id="99a5e-103">Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur ve belirtecin temsil ettiği ortak anahtarı döndürür.</span><span class="sxs-lookup"><span data-stu-id="99a5e-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99a5e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99a5e-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99a5e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99a5e-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="99a5e-106">'ndaki Bütünleştirilmiş kod için Taşınabilir çalıştırılabilir (PE) dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="99a5e-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="99a5e-107">dışı Döndürülen tanımlayıcı ad belirteci.</span><span class="sxs-lookup"><span data-stu-id="99a5e-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="99a5e-108">dışı Tanımlayıcı ad belirtecinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="99a5e-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="99a5e-109">dışı Döndürülen ortak anahtar.</span><span class="sxs-lookup"><span data-stu-id="99a5e-109">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="99a5e-110">dışı Ortak anahtarın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="99a5e-110">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99a5e-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="99a5e-111">Return Value</span></span>  
 <span data-ttu-id="99a5e-112">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="99a5e-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99a5e-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99a5e-113">Remarks</span></span>  
 <span data-ttu-id="99a5e-114">Tanımlayıcı ad belirteci, ortak anahtarın kısaltılmış biçimidir.</span><span class="sxs-lookup"><span data-stu-id="99a5e-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="99a5e-115">Belirteç, derlemeyi imzalamak için kullanılan ortak anahtardan oluşturulan 64 bitlik bir karmadır.</span><span class="sxs-lookup"><span data-stu-id="99a5e-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="99a5e-116">Belirteç, derlemenin tanımlayıcı adının bir parçasıdır ve derleme meta verilerinden okunabilir.</span><span class="sxs-lookup"><span data-stu-id="99a5e-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="99a5e-117">Anahtar alındıktan ve belirteç oluşturulduktan sonra, ayrılan belleği serbest bırakmak için [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodunu çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="99a5e-117">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99a5e-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99a5e-118">Requirements</span></span>  
 <span data-ttu-id="99a5e-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99a5e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99a5e-120">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="99a5e-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="99a5e-121">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="99a5e-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99a5e-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99a5e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99a5e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99a5e-123">See also</span></span>

- [<span data-ttu-id="99a5e-124">StrongNameTokenFromAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99a5e-124">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="99a5e-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99a5e-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
