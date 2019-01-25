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
ms.openlocfilehash: 5ce6478f0331c590a2384a4e7e9b5621c050715d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623644"
---
# <a name="exporttype-method"></a><span data-ttu-id="04ca1-102">ExportType Metodu</span><span class="sxs-lookup"><span data-stu-id="04ca1-102">ExportType Method</span></span>
<span data-ttu-id="04ca1-103">Bir türün dışarı aktarılabilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="04ca1-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04ca1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04ca1-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="04ca1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04ca1-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="04ca1-106">Dışarı aktarmak için derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="04ca1-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="04ca1-107">Belirteç veya derleme kimliği verilebilir türü tanımlayan dosyasının dosya.</span><span class="sxs-lookup"><span data-stu-id="04ca1-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="04ca1-108">Dışarı aktarılabilir hale türünde belirteç.</span><span class="sxs-lookup"><span data-stu-id="04ca1-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="04ca1-109">Dışarı aktarılabilir hale için tam nitelikli tür adı'nı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="04ca1-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="04ca1-110">`ComType` gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="04ca1-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="04ca1-111">Bu parametre için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="04ca1-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="04ca1-112">Dışarı aktarılan tür için belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="04ca1-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04ca1-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="04ca1-113">Return Value</span></span>  
 <span data-ttu-id="04ca1-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="04ca1-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04ca1-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04ca1-115">Requirements</span></span>  
 <span data-ttu-id="04ca1-116">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="04ca1-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04ca1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04ca1-117">See also</span></span>
- [<span data-ttu-id="04ca1-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04ca1-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="04ca1-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04ca1-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="04ca1-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="04ca1-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
