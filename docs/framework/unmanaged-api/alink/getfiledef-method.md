---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5db205993bc1a0665dc0003948ce805813251f48
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787455"
---
# <a name="getfiledef-method"></a><span data-ttu-id="70923-102">GetFileDef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70923-102">GetFileDef Method</span></span>
<span data-ttu-id="70923-103">Meta verilerde kullanılan gerçek FileDef belirtecini alır (ALink tarafından atanan belirtecin aksine).</span><span class="sxs-lookup"><span data-stu-id="70923-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70923-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70923-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="70923-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="70923-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="70923-106">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="70923-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="70923-107">AddFile yönteminden veya AddImport yönteminden alınan eklenen dosyanın belirteci.</span><span class="sxs-lookup"><span data-stu-id="70923-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="70923-108">FileDef belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="70923-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70923-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="70923-109">Return Value</span></span>  
 <span data-ttu-id="70923-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="70923-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70923-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70923-111">Requirements</span></span>  
 <span data-ttu-id="70923-112">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="70923-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70923-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70923-113">See also</span></span>

- [<span data-ttu-id="70923-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70923-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="70923-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70923-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="70923-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="70923-116">ALink API</span></span>](index.md)
