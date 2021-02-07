---
description: 'Daha fazla bilgi edinin: GetFileDef yöntemi'
title: GetFileDef Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
ms.openlocfilehash: 5d44336e686ca565f468fb95ce5290ee41d5e16e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718453"
---
# <a name="getfiledef-method"></a><span data-ttu-id="cce51-103">GetFileDef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cce51-103">GetFileDef Method</span></span>

<span data-ttu-id="cce51-104">Meta verilerde kullanılan gerçek FileDef belirtecini alır (ALink tarafından atanan belirtecin aksine).</span><span class="sxs-lookup"><span data-stu-id="cce51-104">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cce51-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cce51-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="cce51-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cce51-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="cce51-107">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="cce51-107">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="cce51-108">AddFile yönteminden veya AddImport yönteminden alınan eklenen dosyanın belirteci.</span><span class="sxs-lookup"><span data-stu-id="cce51-108">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="cce51-109">FileDef belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="cce51-109">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cce51-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cce51-110">Return Value</span></span>  

 <span data-ttu-id="cce51-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="cce51-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cce51-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cce51-112">Requirements</span></span>  

 <span data-ttu-id="cce51-113">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="cce51-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cce51-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cce51-114">See also</span></span>

- [<span data-ttu-id="cce51-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cce51-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="cce51-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cce51-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="cce51-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="cce51-117">ALink API</span></span>](index.md)
