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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789941"
---
# <a name="exporttype-method"></a><span data-ttu-id="1e0c4-102">ExportType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e0c4-102">ExportType Method</span></span>
<span data-ttu-id="1e0c4-103">Bir türün dışarı aktarılabilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e0c4-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e0c4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e0c4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1e0c4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e0c4-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1e0c4-106">Dışarı aktarmak için derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="1e0c4-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="1e0c4-107">Belirteç veya derleme kimliği verilebilir türü tanımlayan dosyasının dosya.</span><span class="sxs-lookup"><span data-stu-id="1e0c4-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="1e0c4-108">Dışarı aktarılabilir hale türünde belirteç.</span><span class="sxs-lookup"><span data-stu-id="1e0c4-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="1e0c4-109">Dışarı aktarılabilir hale için tam nitelikli tür adı'nı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="1e0c4-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1e0c4-110">`ComType` gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="1e0c4-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="1e0c4-111">Bu parametre için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="1e0c4-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="1e0c4-112">Dışarı aktarılan tür için belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="1e0c4-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e0c4-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1e0c4-113">Return Value</span></span>  
 <span data-ttu-id="1e0c4-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e0c4-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e0c4-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e0c4-115">Requirements</span></span>  
 <span data-ttu-id="1e0c4-116">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="1e0c4-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e0c4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e0c4-117">See also</span></span>

- [<span data-ttu-id="1e0c4-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e0c4-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="1e0c4-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e0c4-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="1e0c4-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="1e0c4-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
