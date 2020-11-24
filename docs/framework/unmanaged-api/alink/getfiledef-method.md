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
ms.openlocfilehash: 42935813579d7f1d55a9f1daf9d8c6c1241f85be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684713"
---
# <a name="getfiledef-method"></a><span data-ttu-id="c480a-102">GetFileDef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c480a-102">GetFileDef Method</span></span>

<span data-ttu-id="c480a-103">Meta verilerde kullanılan gerçek FileDef belirtecini alır (ALink tarafından atanan belirtecin aksine).</span><span class="sxs-lookup"><span data-stu-id="c480a-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c480a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c480a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c480a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c480a-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="c480a-106">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="c480a-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="c480a-107">AddFile yönteminden veya AddImport yönteminden alınan eklenen dosyanın belirteci.</span><span class="sxs-lookup"><span data-stu-id="c480a-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="c480a-108">FileDef belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="c480a-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c480a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c480a-109">Return Value</span></span>  

 <span data-ttu-id="c480a-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="c480a-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c480a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c480a-111">Requirements</span></span>  

 <span data-ttu-id="c480a-112">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="c480a-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c480a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c480a-113">See also</span></span>

- [<span data-ttu-id="c480a-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c480a-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c480a-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c480a-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c480a-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="c480a-116">ALink API</span></span>](index.md)
