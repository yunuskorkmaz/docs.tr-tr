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
ms.openlocfilehash: ef7d6272c04c3edab8ef652bcb2759861ff2b982
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129577"
---
# <a name="embedresource-method"></a><span data-ttu-id="3d528-102">EmbedResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d528-102">EmbedResource Method</span></span>
<span data-ttu-id="3d528-103">Katıştırılmış bir kaynağı bildirir.</span><span class="sxs-lookup"><span data-stu-id="3d528-103">Declares an embedded resource.</span></span> <span data-ttu-id="3d528-104">Bu yöntem kaynağın gerçekten ekleme değil.</span><span class="sxs-lookup"><span data-stu-id="3d528-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d528-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d528-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d528-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d528-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3d528-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="3d528-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3d528-108">Belirteç veya derleme Kimliğini içeren kaynak dosyasının dosya.</span><span class="sxs-lookup"><span data-stu-id="3d528-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="3d528-109">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="3d528-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="3d528-110">RVA kaynaktan uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="3d528-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3d528-111">Erişilebilirlik bayrakları gibi `mrPublic` ve `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="3d528-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="3d528-112">Bu bayrak için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="3d528-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d528-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3d528-113">Return Value</span></span>  
 <span data-ttu-id="3d528-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d528-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d528-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d528-115">Requirements</span></span>  
 <span data-ttu-id="3d528-116">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3d528-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d528-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d528-117">See also</span></span>

- [<span data-ttu-id="3d528-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d528-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="3d528-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d528-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="3d528-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="3d528-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
