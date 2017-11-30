---
title: invalidIUnknown MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 04fdc96168823397296449ebc25ccdded1ea55c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="97444-102">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="97444-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="97444-103">`invalidIUnknown` Yönetilen hata ayıklama Yardımcısı (MDA) geçersiz bir zaman etkinleştirilirse `IUnknown` işaretçi yerel koddan yönetilen koda geçirilir.</span><span class="sxs-lookup"><span data-stu-id="97444-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="97444-104">`IUnknown` İçin sorgulandığında başarı döndürülecek başarısız `IUnknown` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="97444-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="97444-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="97444-105">Symptoms</span></span>  
 <span data-ttu-id="97444-106">Bağımsız değişken sıralama sırasında bir COM arabirimi işaretçisi hazırlama beklenmeyen bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="97444-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="97444-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="97444-107">Cause</span></span>  
 <span data-ttu-id="97444-108">Yanlış bir `QueryInterface` COM arabirimi üzerindeki uygulama için CLR geçirildi.</span><span class="sxs-lookup"><span data-stu-id="97444-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="97444-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="97444-109">Resolution</span></span>  
 <span data-ttu-id="97444-110">Düzeltmek `QueryInterface` uygulaması.</span><span class="sxs-lookup"><span data-stu-id="97444-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="97444-111">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="97444-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="97444-112">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="97444-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="97444-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="97444-113">Output</span></span>  
 <span data-ttu-id="97444-114">Hatanın açıklaması.</span><span class="sxs-lookup"><span data-stu-id="97444-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="97444-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="97444-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="97444-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97444-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="97444-117">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="97444-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="97444-118">Birlikte çalışma hazırlama</span><span class="sxs-lookup"><span data-stu-id="97444-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
