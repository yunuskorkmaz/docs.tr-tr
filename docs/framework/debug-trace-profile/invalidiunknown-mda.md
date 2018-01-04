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
ms.workload: dotnet
ms.openlocfilehash: ff88f8bc544c95a4fe5149cd517d9157d5ac23c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="216f9-102">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="216f9-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="216f9-103">`invalidIUnknown` Yönetilen hata ayıklama Yardımcısı (MDA) geçersiz bir zaman etkinleştirilirse `IUnknown` işaretçi yerel koddan yönetilen koda geçirilir.</span><span class="sxs-lookup"><span data-stu-id="216f9-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="216f9-104">`IUnknown` İçin sorgulandığında başarı döndürülecek başarısız `IUnknown` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="216f9-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="216f9-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="216f9-105">Symptoms</span></span>  
 <span data-ttu-id="216f9-106">Bağımsız değişken sıralama sırasında bir COM arabirimi işaretçisi hazırlama beklenmeyen bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="216f9-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="216f9-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="216f9-107">Cause</span></span>  
 <span data-ttu-id="216f9-108">Yanlış bir `QueryInterface` COM arabirimi üzerindeki uygulama için CLR geçirildi.</span><span class="sxs-lookup"><span data-stu-id="216f9-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="216f9-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="216f9-109">Resolution</span></span>  
 <span data-ttu-id="216f9-110">Düzeltmek `QueryInterface` uygulaması.</span><span class="sxs-lookup"><span data-stu-id="216f9-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="216f9-111">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="216f9-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="216f9-112">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="216f9-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="216f9-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="216f9-113">Output</span></span>  
 <span data-ttu-id="216f9-114">Hatanın açıklaması.</span><span class="sxs-lookup"><span data-stu-id="216f9-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="216f9-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="216f9-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="216f9-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="216f9-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="216f9-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="216f9-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="216f9-118">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="216f9-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
