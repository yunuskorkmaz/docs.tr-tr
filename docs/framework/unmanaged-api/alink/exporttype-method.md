---
title: ExportType Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95ff27143453e7772b4a463fa66ca039bbb715fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226923"
---
# <a name="exporttype-method"></a><span data-ttu-id="e71b5-102">ExportType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e71b5-102">ExportType Method</span></span>
<span data-ttu-id="e71b5-103">Bir türün dışarı aktarılabilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e71b5-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e71b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e71b5-104">Syntax</span></span>  
  
```  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e71b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e71b5-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e71b5-106">Dışarı aktarmak için derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="e71b5-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e71b5-107">Belirteç veya derleme kimliği verilebilir türü tanımlayan dosyasının dosya.</span><span class="sxs-lookup"><span data-stu-id="e71b5-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="e71b5-108">Dışarı aktarılabilir hale türünde belirteç.</span><span class="sxs-lookup"><span data-stu-id="e71b5-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="e71b5-109">Dışarı aktarılabilir hale için tam nitelikli tür adı'nı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e71b5-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 `ComType` <span data-ttu-id="e71b5-110">gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="e71b5-110">flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="e71b5-111">Bu parametre için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="e71b5-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="e71b5-112">Dışarı aktarılan tür için belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="e71b5-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e71b5-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e71b5-113">Return Value</span></span>  
 <span data-ttu-id="e71b5-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="e71b5-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e71b5-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e71b5-115">Requirements</span></span>  
 <span data-ttu-id="e71b5-116">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="e71b5-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e71b5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e71b5-117">See also</span></span>

- [<span data-ttu-id="e71b5-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e71b5-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e71b5-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e71b5-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e71b5-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="e71b5-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
