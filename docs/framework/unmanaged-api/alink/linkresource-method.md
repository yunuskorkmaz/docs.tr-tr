---
title: LinkResource Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
ms.openlocfilehash: 4f2f13976dfd4e5601bf8b54bed7b851884fbb9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690453"
---
# <a name="linkresource-method"></a><span data-ttu-id="a50d9-102">LinkResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a50d9-102">LinkResource Method</span></span>

<span data-ttu-id="a50d9-103">Bir kaynaktaki bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="a50d9-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a50d9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a50d9-104">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a50d9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a50d9-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="a50d9-106">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a50d9-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="a50d9-107">Dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="a50d9-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="a50d9-108">İsteğe bağlı yeni dosya adı.</span><span class="sxs-lookup"><span data-stu-id="a50d9-108">Optional new file name.</span></span> <span data-ttu-id="a50d9-109">NULL olmayan bir değer, `pszFileName` pszNewLocation ' a kopyalanacaktır.</span><span class="sxs-lookup"><span data-stu-id="a50d9-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="a50d9-110">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="a50d9-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a50d9-111">Ve gibi erişilebilirlik bayrakları `mrPublic` `mrPrivate` .</span><span class="sxs-lookup"><span data-stu-id="a50d9-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="a50d9-112">Bu parametre [DefineManifestResource metoduna](../metadata/imetadataassemblyemit-definemanifestresource-method.md)geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a50d9-112">This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a50d9-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a50d9-113">Return Value</span></span>  

 <span data-ttu-id="a50d9-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="a50d9-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a50d9-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a50d9-115">Requirements</span></span>  

 <span data-ttu-id="a50d9-116">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a50d9-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a50d9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a50d9-117">See also</span></span>

- [<span data-ttu-id="a50d9-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a50d9-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a50d9-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a50d9-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a50d9-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="a50d9-120">ALink API</span></span>](index.md)
