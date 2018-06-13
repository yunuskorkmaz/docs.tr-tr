---
title: invalidIUnknown MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db360a3b7c5f70596d5d5855b8e38dae5d484c42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390181"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="a8d95-102">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="a8d95-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="a8d95-103">`invalidIUnknown` Yönetilen hata ayıklama Yardımcısı (MDA) geçersiz bir zaman etkinleştirilirse `IUnknown` işaretçi yerel koddan yönetilen koda geçirilir.</span><span class="sxs-lookup"><span data-stu-id="a8d95-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="a8d95-104">`IUnknown` İçin sorgulandığında başarı döndürülecek başarısız `IUnknown` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a8d95-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a8d95-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="a8d95-105">Symptoms</span></span>  
 <span data-ttu-id="a8d95-106">Bağımsız değişken sıralama sırasında bir COM arabirimi işaretçisi hazırlama beklenmeyen bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="a8d95-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a8d95-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="a8d95-107">Cause</span></span>  
 <span data-ttu-id="a8d95-108">Yanlış bir `QueryInterface` COM arabirimi üzerindeki uygulama için CLR geçirildi.</span><span class="sxs-lookup"><span data-stu-id="a8d95-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a8d95-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="a8d95-109">Resolution</span></span>  
 <span data-ttu-id="a8d95-110">Düzeltmek `QueryInterface` uygulaması.</span><span class="sxs-lookup"><span data-stu-id="a8d95-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a8d95-111">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="a8d95-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="a8d95-112">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a8d95-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a8d95-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="a8d95-113">Output</span></span>  
 <span data-ttu-id="a8d95-114">Hatanın açıklaması.</span><span class="sxs-lookup"><span data-stu-id="a8d95-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a8d95-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a8d95-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8d95-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8d95-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="a8d95-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="a8d95-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="a8d95-118">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="a8d95-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
