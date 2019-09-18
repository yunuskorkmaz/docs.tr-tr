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
ms.openlocfilehash: ea7f48ab61c16cb0430717074f1b1feab4827763
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052601"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="e1233-102">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="e1233-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="e1233-103">Yerel koddan yönetilen koda geçersiz `IUnknown` bir işaretçi geçirildiğinde yönetilenhataayıklamaYardımcısı(MDA)etkinleştirilir.`invalidIUnknown`</span><span class="sxs-lookup"><span data-stu-id="e1233-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="e1233-104">Arabirim için sorgulandığında başarı geri dönemezse.`IUnknown` `IUnknown`</span><span class="sxs-lookup"><span data-stu-id="e1233-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e1233-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="e1233-105">Symptoms</span></span>  
 <span data-ttu-id="e1233-106">Bağımsız değişken sıralaması sırasında COM arabirim işaretçisi sıralaması sırasında beklenmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e1233-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e1233-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="e1233-107">Cause</span></span>  
 <span data-ttu-id="e1233-108">CLR 'ye `QueryInterface` geçirilen com arabiriminde yanlış bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="e1233-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e1233-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="e1233-109">Resolution</span></span>  
 <span data-ttu-id="e1233-110">`QueryInterface` Uygulamayı düzeltin.</span><span class="sxs-lookup"><span data-stu-id="e1233-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e1233-111">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="e1233-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="e1233-112">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e1233-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e1233-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="e1233-113">Output</span></span>  
 <span data-ttu-id="e1233-114">Hatanın açıklaması.</span><span class="sxs-lookup"><span data-stu-id="e1233-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e1233-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e1233-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1233-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1233-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e1233-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="e1233-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e1233-118">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="e1233-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
