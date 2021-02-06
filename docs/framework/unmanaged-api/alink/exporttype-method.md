---
description: 'Daha fazla bilgi edinin: ExportType Yöntemi'
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
ms.openlocfilehash: 6dc047cac3b80e6fe7a6f2cd980061b34bb7f286
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638073"
---
# <a name="exporttype-method"></a><span data-ttu-id="86734-103">ExportType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86734-103">ExportType Method</span></span>

<span data-ttu-id="86734-104">Bir türün verilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="86734-104">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86734-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86734-105">Syntax</span></span>  
  
```cpp  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="86734-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86734-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="86734-107">Dışarı aktarılacak derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="86734-107">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="86734-108">Dışarı aktarılabilir türü tanımlayan dosyanın dosya belirteci veya derleme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="86734-108">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="86734-109">Dışarı aktarılabilir yapılacak tür belirteci.</span><span class="sxs-lookup"><span data-stu-id="86734-109">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="86734-110">Dışarı aktarılabilir hale getirmek için tam tür adı.</span><span class="sxs-lookup"><span data-stu-id="86734-110">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="86734-111">`ComType` veya gibi bayraklar `tdPublic` `tdNested` .</span><span class="sxs-lookup"><span data-stu-id="86734-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="86734-112">Bu parametre [DefineExportedType yöntemine](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="86734-112">This parameter may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="86734-113">İçe aktarılmış tür için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="86734-113">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86734-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="86734-114">Return Value</span></span>  

 <span data-ttu-id="86734-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="86734-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86734-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86734-116">Requirements</span></span>  

 <span data-ttu-id="86734-117">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="86734-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86734-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86734-118">See also</span></span>

- [<span data-ttu-id="86734-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86734-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="86734-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86734-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="86734-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="86734-121">ALink API</span></span>](index.md)
