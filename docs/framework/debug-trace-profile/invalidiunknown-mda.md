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
ms.openlocfilehash: 5df9a3f506d8c2de6f1a3125459adc2d59d510bf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217361"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="f1648-102">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="f1648-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="f1648-103">`invalidIUnknown` yönetilen hata ayıklama Yardımcısı (MDA), yerel koddan yönetilen koda geçersiz bir `IUnknown` işaretçisi geçirildiğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f1648-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="f1648-104">`IUnknown`, `IUnknown` arabirimi için sorgulandığında başarıyı geri döndüremiyor.</span><span class="sxs-lookup"><span data-stu-id="f1648-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f1648-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="f1648-105">Symptoms</span></span>  
 <span data-ttu-id="f1648-106">Bağımsız değişken sıralaması sırasında COM arabirim işaretçisi sıralaması sırasında beklenmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f1648-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f1648-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="f1648-107">Cause</span></span>  
 <span data-ttu-id="f1648-108">CLR 'ye geçirilen COM arabiriminde yanlış bir `QueryInterface` uygulama.</span><span class="sxs-lookup"><span data-stu-id="f1648-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f1648-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="f1648-109">Resolution</span></span>  
 <span data-ttu-id="f1648-110">`QueryInterface` uygulamasını düzeltin.</span><span class="sxs-lookup"><span data-stu-id="f1648-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f1648-111">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="f1648-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="f1648-112">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f1648-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f1648-113">Çıktı</span><span class="sxs-lookup"><span data-stu-id="f1648-113">Output</span></span>  
 <span data-ttu-id="f1648-114">Hatanın açıklaması.</span><span class="sxs-lookup"><span data-stu-id="f1648-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f1648-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f1648-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1648-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1648-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f1648-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="f1648-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f1648-118">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="f1648-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
