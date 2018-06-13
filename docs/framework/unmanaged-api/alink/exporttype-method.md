---
title: ExportType Metodu
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
ms.openlocfilehash: 958b56266b0d2dcc317204c39a1df56baabd83e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402489"
---
# <a name="exporttype-method"></a><span data-ttu-id="e5832-102">ExportType Metodu</span><span class="sxs-lookup"><span data-stu-id="e5832-102">ExportType Method</span></span>
<span data-ttu-id="e5832-103">Bir tür verilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5832-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5832-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5832-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="e5832-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5832-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e5832-106">Dışarı aktarmak için derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="e5832-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e5832-107">Dosya belirteç veya derleme kimliği dosyasının dışarı aktarılabilir türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e5832-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="e5832-108">Dışarı aktarılabilir yapılması türünde belirteç.</span><span class="sxs-lookup"><span data-stu-id="e5832-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="e5832-109">Dışarı aktarılabilir duruma getirilmek üzere tam olarak nitelenmiş tür adı.</span><span class="sxs-lookup"><span data-stu-id="e5832-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e5832-110">`ComType` gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="e5832-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="e5832-111">Bu parametre için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="e5832-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="e5832-112">Dışarı aktarılan tür için belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="e5832-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5832-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e5832-113">Return Value</span></span>  
 <span data-ttu-id="e5832-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5832-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5832-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5832-115">Requirements</span></span>  
 <span data-ttu-id="e5832-116">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="e5832-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5832-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5832-117">See Also</span></span>  
 [<span data-ttu-id="e5832-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5832-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e5832-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5832-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e5832-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="e5832-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
