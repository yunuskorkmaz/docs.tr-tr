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
ms.openlocfilehash: 35560b966d5fba60ac35b2eb1e559e196fc868f5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754549"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="05a9c-102">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="05a9c-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="05a9c-103">`invalidIUnknown` Yönetilen hata ayıklama Yardımcısı (MDA) geçersiz olduğunda etkinleştirilir `IUnknown` işaretçi yönetilen koda yerel koddan geçirilir.</span><span class="sxs-lookup"><span data-stu-id="05a9c-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="05a9c-104">`IUnknown` İçin sorgulandığında başarı döndüremediğine `IUnknown` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="05a9c-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="05a9c-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="05a9c-105">Symptoms</span></span>  
 <span data-ttu-id="05a9c-106">Bağımsız değişken sıralama sırasında bir COM arabirimi işaretçisini hazırlama beklenmeyen bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="05a9c-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="05a9c-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="05a9c-107">Cause</span></span>  
 <span data-ttu-id="05a9c-108">Yanlış bir `QueryInterface` COM arabirimi mantığınız CLR geçirildi.</span><span class="sxs-lookup"><span data-stu-id="05a9c-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="05a9c-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="05a9c-109">Resolution</span></span>  
 <span data-ttu-id="05a9c-110">Düzeltme `QueryInterface` uygulaması.</span><span class="sxs-lookup"><span data-stu-id="05a9c-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="05a9c-111">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="05a9c-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="05a9c-112">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="05a9c-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="05a9c-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="05a9c-113">Output</span></span>  
 <span data-ttu-id="05a9c-114">Hatanın açıklaması.</span><span class="sxs-lookup"><span data-stu-id="05a9c-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="05a9c-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="05a9c-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="05a9c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05a9c-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="05a9c-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="05a9c-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="05a9c-118">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="05a9c-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
