---
description: 'Daha fazla bilgi edinin: EmitAssembly yöntemi'
title: EmitAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
ms.openlocfilehash: aada17d8df6435c5edfe6beb5db5ee13f887f253
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638346"
---
# <a name="emitassembly-method"></a><span data-ttu-id="9f6ba-103">EmitAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f6ba-103">EmitAssembly Method</span></span>

<span data-ttu-id="9f6ba-104">Derlemeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f6ba-104">Creates the assembly.</span></span> <span data-ttu-id="9f6ba-105">Derleme dosyası hariç diğer tüm dosyalar kapatıldıktan sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="9f6ba-105">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="9f6ba-106">İlişkisiz modüller üretilirken bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="9f6ba-106">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f6ba-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f6ba-107">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f6ba-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f6ba-108">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="9f6ba-109">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9f6ba-109">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f6ba-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9f6ba-110">Return Value</span></span>  

 <span data-ttu-id="9f6ba-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f6ba-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f6ba-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f6ba-112">Requirements</span></span>  

 <span data-ttu-id="9f6ba-113">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="9f6ba-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f6ba-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f6ba-114">See also</span></span>

- [<span data-ttu-id="9f6ba-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f6ba-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9f6ba-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f6ba-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="9f6ba-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="9f6ba-117">ALink API</span></span>](index.md)
