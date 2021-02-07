---
description: 'Daha fazla bilgi edinin: LinkResource yöntemi'
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
ms.openlocfilehash: ff12138433577eccbb313b8e64a329be1358ba70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662552"
---
# <a name="linkresource-method"></a><span data-ttu-id="91652-103">LinkResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91652-103">LinkResource Method</span></span>

<span data-ttu-id="91652-104">Bir kaynaktaki bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="91652-104">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91652-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91652-105">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="91652-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91652-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="91652-107">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="91652-107">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="91652-108">Dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="91652-108">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="91652-109">İsteğe bağlı yeni dosya adı.</span><span class="sxs-lookup"><span data-stu-id="91652-109">Optional new file name.</span></span> <span data-ttu-id="91652-110">NULL olmayan bir değer, `pszFileName` pszNewLocation ' a kopyalanacaktır.</span><span class="sxs-lookup"><span data-stu-id="91652-110">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="91652-111">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="91652-111">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="91652-112">Ve gibi erişilebilirlik bayrakları `mrPublic` `mrPrivate` .</span><span class="sxs-lookup"><span data-stu-id="91652-112">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="91652-113">Bu parametre [DefineManifestResource metoduna](../metadata/imetadataassemblyemit-definemanifestresource-method.md)geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="91652-113">This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91652-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="91652-114">Return Value</span></span>  

 <span data-ttu-id="91652-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="91652-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91652-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91652-116">Requirements</span></span>  

 <span data-ttu-id="91652-117">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="91652-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91652-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91652-118">See also</span></span>

- [<span data-ttu-id="91652-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91652-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="91652-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91652-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="91652-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="91652-121">ALink API</span></span>](index.md)
