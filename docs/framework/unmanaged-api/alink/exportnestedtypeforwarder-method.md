---
title: ExportNestedTypeForwarder Metodu
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 050ed0bbd4da38bede5a56ff95d0243f5f3cf1da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220090"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="ee036-102">ExportNestedTypeForwarder Metodu</span><span class="sxs-lookup"><span data-stu-id="ee036-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="ee036-103">Bir iç içe geçmiş bir tür ileticisi verilen derleme türü tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="ee036-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee036-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee036-104">Syntax</span></span>  
  
```  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee036-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ee036-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ee036-106">Dışarı aktarmak için derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="ee036-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ee036-107">Belirteç veya derleme kimliği türü tanımlayan dosyasının dosya.</span><span class="sxs-lookup"><span data-stu-id="ee036-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="ee036-108">Belirteç türü.</span><span class="sxs-lookup"><span data-stu-id="ee036-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="ee036-109">Üst tür belirteci.</span><span class="sxs-lookup"><span data-stu-id="ee036-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="ee036-110">Dışarı aktarmak için tam nitelikli tür adı.</span><span class="sxs-lookup"><span data-stu-id="ee036-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 `ComType` <span data-ttu-id="ee036-111">gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="ee036-111">flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="ee036-112">Dışarı aktarma türü belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="ee036-112">Receives token of export type.</span></span> <span data-ttu-id="ee036-113">Bu, iç içe geçmiş türler yalnızca yayma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ee036-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee036-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ee036-114">Return Value</span></span>  
 <span data-ttu-id="ee036-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="ee036-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee036-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee036-116">Requirements</span></span>  
 <span data-ttu-id="ee036-117">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="ee036-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee036-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee036-118">See also</span></span>

- [<span data-ttu-id="ee036-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee036-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="ee036-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee036-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="ee036-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="ee036-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
