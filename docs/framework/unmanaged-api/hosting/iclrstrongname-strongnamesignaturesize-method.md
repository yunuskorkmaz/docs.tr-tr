---
title: ICLRStrongName::StrongNameSignatureSize Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0c81b51deb6affb3dd39677184ea0a4b2e6ff61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219986"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="87986-102">ICLRStrongName::StrongNameSignatureSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87986-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="87986-103">Tanımlayıcı ad imzası boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="87986-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="87986-104">Bu yöntem, genellikle dosyasında gecikmeli imzalanmış bir derlemeyi oluştururken ayırmak için ne kadar alan olmadığının derleyiciler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87986-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87986-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87986-105">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="87986-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87986-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="87986-107">[in] Türünden bir yapıyı [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) tanımlayıcı ad imzası oluşturmak için kullanılan anahtar çiftinden ortak kısmını içerir.</span><span class="sxs-lookup"><span data-stu-id="87986-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="87986-108">[in] Bayt cinsinden boyutu, `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="87986-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="87986-109">[in] Tanımlayıcı ad imzası depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="87986-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87986-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="87986-110">Return Value</span></span>  
 <span data-ttu-id="87986-111">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="87986-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87986-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87986-112">Requirements</span></span>  
 <span data-ttu-id="87986-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87986-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87986-114">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="87986-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="87986-115">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="87986-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87986-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87986-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87986-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87986-117">See also</span></span>

- [<span data-ttu-id="87986-118">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87986-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
