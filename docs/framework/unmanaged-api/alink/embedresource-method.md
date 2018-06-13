---
title: EmbedResource Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb1fc266c8451953c8b6a9c686f4a1c1951966e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405404"
---
# <a name="embedresource-method"></a><span data-ttu-id="9557f-102">EmbedResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9557f-102">EmbedResource Method</span></span>
<span data-ttu-id="9557f-103">Katıştırılmış bir kaynağı bildirir.</span><span class="sxs-lookup"><span data-stu-id="9557f-103">Declares an embedded resource.</span></span> <span data-ttu-id="9557f-104">Bu yöntem kaynağın gerçekte katıştırmak değil.</span><span class="sxs-lookup"><span data-stu-id="9557f-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9557f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9557f-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9557f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9557f-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9557f-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="9557f-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="9557f-108">Dosya belirteci ya da derleme kaynağı içeren dosyanın kimliği.</span><span class="sxs-lookup"><span data-stu-id="9557f-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="9557f-109">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="9557f-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="9557f-110">RVA kaynaktan uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="9557f-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9557f-111">Erişilebilirlik bayrakları gibi `mrPublic` ve `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="9557f-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="9557f-112">Bu bayrakların geçirilen [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="9557f-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9557f-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9557f-113">Return Value</span></span>  
 <span data-ttu-id="9557f-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="9557f-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9557f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9557f-115">Requirements</span></span>  
 <span data-ttu-id="9557f-116">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9557f-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9557f-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9557f-117">See Also</span></span>  
 [<span data-ttu-id="9557f-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9557f-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="9557f-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9557f-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="9557f-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="9557f-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
