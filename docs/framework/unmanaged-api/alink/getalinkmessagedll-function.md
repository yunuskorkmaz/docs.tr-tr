---
title: GetALinkMessageDll İşlevi
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 323e53c45a26d5703548ebe9863978f6d3929f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787467"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="a97d3-102">GetALinkMessageDll İşlevi</span><span class="sxs-lookup"><span data-stu-id="a97d3-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="a97d3-103">İleti DLL 'sini bulur ve yükler.</span><span class="sxs-lookup"><span data-stu-id="a97d3-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="a97d3-104">İleti DLL dosyası bulunamıyorsa veya yüklenemezse 0 döndürür.</span><span class="sxs-lookup"><span data-stu-id="a97d3-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="a97d3-105">İleti DLL 'SI, adı bir dil KIMLIĞI, ya da geçerli dizinde olan bir alt dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a97d3-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a97d3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a97d3-106">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="a97d3-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a97d3-107">Requirements</span></span>  
 <span data-ttu-id="a97d3-108">**Üstbilgi:** ALink. h</span><span class="sxs-lookup"><span data-stu-id="a97d3-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="a97d3-109">**Kitaplık**: ALink. dll</span><span class="sxs-lookup"><span data-stu-id="a97d3-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a97d3-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a97d3-110">See also</span></span>

- [<span data-ttu-id="a97d3-111">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="a97d3-111">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
