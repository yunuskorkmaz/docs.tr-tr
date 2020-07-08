---
title: invalidIUnknown MDA
description: Yerel koddan yönetilen koda geçersiz bir IUnknown işaretçisi geçirildiğinde etkinleştirilen invalidIUnknown Managed hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
ms.openlocfilehash: 65d704463ed746390ff1710b590bf080013bf53d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051733"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="b71ea-103">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="b71ea-103">invalidIUnknown MDA</span></span>
<span data-ttu-id="b71ea-104">`invalidIUnknown`Yerel koddan yönetilen koda geçersiz bir işaretçi geçirildiğinde yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir `IUnknown` .</span><span class="sxs-lookup"><span data-stu-id="b71ea-104">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="b71ea-105">`IUnknown`Arabirim için sorgulandığında başarı geri dönemezse `IUnknown` .</span><span class="sxs-lookup"><span data-stu-id="b71ea-105">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b71ea-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="b71ea-106">Symptoms</span></span>  
 <span data-ttu-id="b71ea-107">Bağımsız değişken sıralaması sırasında COM arabirim işaretçisi sıralaması sırasında beklenmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b71ea-107">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b71ea-108">Nedeni</span><span class="sxs-lookup"><span data-stu-id="b71ea-108">Cause</span></span>  
 <span data-ttu-id="b71ea-109">`QueryInterface`Clr 'ye GEÇIRILEN com arabiriminde yanlış bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="b71ea-109">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b71ea-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="b71ea-110">Resolution</span></span>  
 <span data-ttu-id="b71ea-111">Uygulamayı düzeltin `QueryInterface` .</span><span class="sxs-lookup"><span data-stu-id="b71ea-111">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b71ea-112">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="b71ea-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="b71ea-113">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b71ea-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b71ea-114">Çıktı</span><span class="sxs-lookup"><span data-stu-id="b71ea-114">Output</span></span>  
 <span data-ttu-id="b71ea-115">Hatanın açıklaması.</span><span class="sxs-lookup"><span data-stu-id="b71ea-115">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b71ea-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b71ea-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b71ea-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b71ea-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="b71ea-118">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="b71ea-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="b71ea-119">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="b71ea-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
