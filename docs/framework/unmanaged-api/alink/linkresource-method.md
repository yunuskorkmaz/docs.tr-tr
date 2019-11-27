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
ms.openlocfilehash: 9e91d990a8f23335248043c59eb210e8c4155e3a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445624"
---
# <a name="linkresource-method"></a><span data-ttu-id="b6aee-102">LinkResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6aee-102">LinkResource Method</span></span>
<span data-ttu-id="b6aee-103">Bir kaynaktaki bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="b6aee-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6aee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6aee-104">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6aee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6aee-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b6aee-106">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b6aee-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="b6aee-107">Dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="b6aee-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="b6aee-108">İsteğe bağlı yeni dosya adı.</span><span class="sxs-lookup"><span data-stu-id="b6aee-108">Optional new file name.</span></span> <span data-ttu-id="b6aee-109">NULL olmayan `pszFileName`, pszNewLocation ' a kopyalanacaktır.</span><span class="sxs-lookup"><span data-stu-id="b6aee-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="b6aee-110">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="b6aee-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b6aee-111">`mrPublic` ve `mrPrivate`gibi erişilebilirlik bayrakları.</span><span class="sxs-lookup"><span data-stu-id="b6aee-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="b6aee-112">Bu parametre [DefineManifestResource metoduna](../metadata/imetadataassemblyemit-definemanifestresource-method.md)geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b6aee-112">This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6aee-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b6aee-113">Return Value</span></span>  
 <span data-ttu-id="b6aee-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="b6aee-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6aee-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6aee-115">Requirements</span></span>  
 <span data-ttu-id="b6aee-116">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b6aee-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6aee-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6aee-117">See also</span></span>

- [<span data-ttu-id="b6aee-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6aee-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b6aee-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6aee-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b6aee-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="b6aee-120">ALink API</span></span>](index.md)
