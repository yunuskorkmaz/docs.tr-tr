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
ms.openlocfilehash: eb8112d6d2b5c2cbb257db2f20ff4be5a84e827b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787478"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="91d6f-102">ExportNestedTypeForwarder Metodu</span><span class="sxs-lookup"><span data-stu-id="91d6f-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="91d6f-103">İç içe geçmiş bir tür için verilen derlemenin tür tablosuna bir tür ileticisi ekler.</span><span class="sxs-lookup"><span data-stu-id="91d6f-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91d6f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91d6f-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="91d6f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91d6f-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="91d6f-106">Dışarı aktarılacak derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="91d6f-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="91d6f-107">Türü tanımlayan dosyanın belirteç veya derleme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="91d6f-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="91d6f-108">Tür için belirteç.</span><span class="sxs-lookup"><span data-stu-id="91d6f-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="91d6f-109">Üst tür belirteci.</span><span class="sxs-lookup"><span data-stu-id="91d6f-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="91d6f-110">Dışarı aktarılacak tam tür adı.</span><span class="sxs-lookup"><span data-stu-id="91d6f-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="91d6f-111">`ComType``tdPublic` veya`tdNested`gibi bayraklar.</span><span class="sxs-lookup"><span data-stu-id="91d6f-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="91d6f-112">Dışarı aktarma türünün belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="91d6f-112">Receives token of export type.</span></span> <span data-ttu-id="91d6f-113">Bu yalnızca iç içe geçmiş türleri yayma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="91d6f-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91d6f-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="91d6f-114">Return Value</span></span>  
 <span data-ttu-id="91d6f-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="91d6f-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91d6f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91d6f-116">Requirements</span></span>  
 <span data-ttu-id="91d6f-117">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="91d6f-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d6f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91d6f-118">See also</span></span>

- [<span data-ttu-id="91d6f-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91d6f-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="91d6f-120">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91d6f-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="91d6f-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="91d6f-121">ALink API</span></span>](index.md)
