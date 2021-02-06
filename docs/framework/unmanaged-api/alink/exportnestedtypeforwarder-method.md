---
description: 'Şu konuda daha fazla bilgi edinin: ExportNestedTypeForwarder yöntemi'
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
ms.openlocfilehash: fd791e3fea76338f191fcf924d56720d257d2e8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638112"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="a636f-103">ExportNestedTypeForwarder Metodu</span><span class="sxs-lookup"><span data-stu-id="a636f-103">ExportNestedTypeForwarder Method</span></span>

<span data-ttu-id="a636f-104">İç içe geçmiş bir tür için verilen derlemenin tür tablosuna bir tür ileticisi ekler.</span><span class="sxs-lookup"><span data-stu-id="a636f-104">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a636f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a636f-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a636f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a636f-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="a636f-107">Dışarı aktarılacak derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a636f-107">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="a636f-108">Türü tanımlayan dosyanın belirteç veya derleme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a636f-108">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="a636f-109">Tür için belirteç.</span><span class="sxs-lookup"><span data-stu-id="a636f-109">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="a636f-110">Üst tür belirteci.</span><span class="sxs-lookup"><span data-stu-id="a636f-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="a636f-111">Dışarı aktarılacak tam tür adı.</span><span class="sxs-lookup"><span data-stu-id="a636f-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a636f-112">`ComType` veya gibi bayraklar `tdPublic` `tdNested` .</span><span class="sxs-lookup"><span data-stu-id="a636f-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="a636f-113">Dışarı aktarma türünün belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="a636f-113">Receives token of export type.</span></span> <span data-ttu-id="a636f-114">Bu yalnızca iç içe geçmiş türleri yayma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a636f-114">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a636f-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a636f-115">Return Value</span></span>  

 <span data-ttu-id="a636f-116">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="a636f-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a636f-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a636f-117">Requirements</span></span>  

 <span data-ttu-id="a636f-118">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="a636f-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a636f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a636f-119">See also</span></span>

- [<span data-ttu-id="a636f-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a636f-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a636f-121">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a636f-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a636f-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="a636f-122">ALink API</span></span>](index.md)
