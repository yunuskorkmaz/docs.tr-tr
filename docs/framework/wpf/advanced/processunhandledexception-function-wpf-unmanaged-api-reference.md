---
title: "ProcessUnhandledException işlevi (WPF yönetilmeyen API Başvurusu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ProcessUnhandledException
api_location: PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8328ae4bcbff54743e8df0a4b6ff6da3065ea470
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="40790-102">ProcessUnhandledException işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="40790-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="40790-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="40790-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="40790-104">Windows Presentation Foundation (WPF) altyapısı tarafından özel durum işleme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40790-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40790-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40790-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40790-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40790-106">Parameters</span></span>  
 <span data-ttu-id="40790-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="40790-107">errorMsg</span></span>  
 <span data-ttu-id="40790-108">Hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="40790-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40790-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40790-109">Requirements</span></span>  
 <span data-ttu-id="40790-110">**Platformlar:** bkz [.NET Framework sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40790-110">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40790-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="40790-111">**DLL:**</span></span>  
  
 <span data-ttu-id="40790-112">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="40790-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="40790-113">.NET Framework 4 ve üzeri: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="40790-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="40790-114">**.NET framework sürümü:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40790-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40790-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40790-115">See Also</span></span>  
 [<span data-ttu-id="40790-116">WPF yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="40790-116">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
