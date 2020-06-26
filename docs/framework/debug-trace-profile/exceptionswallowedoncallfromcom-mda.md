---
title: exceptionSwallowedOnCallFromCom MDA
description: .NET 'teki exceptionSwallowedOnCallFromCOM Managed hata ayıklama Yardımcısı ' nı gözden geçirin. Bu MDA, bir özel durum oluşturulursa, ancak bunu raporlamak için iyi bir yol olmadığında meydana gelir.
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
ms.openlocfilehash: 434f06cf953147d5c245e625db997bed6dbef700
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415959"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="c826b-104">exceptionSwallowedOnCallFromCom MDA</span><span class="sxs-lookup"><span data-stu-id="c826b-104">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="c826b-105">`exceptionSwallowedOnCallFromCOM`Yönetilen hata ayıklama Yardımcısı (MDA), yönetilmeyen BIR HRESULT dönüş türüne sahip olmayan bir yöntem aracılığıyla com 'dan çağrılan ortak dil çalışma zamanı (CLR) kodundan bir özel durum oluştuğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c826b-105">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c826b-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="c826b-106">Symptoms</span></span>  
 <span data-ttu-id="c826b-107">COM 'tan yönetilen bileşen çağrısı, FALSE veya 0 değeri ile döndürür.</span><span class="sxs-lookup"><span data-stu-id="c826b-107">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="c826b-108">Alternatif olarak, yöntemin bir void dönüş türü varsa, yöntemin yürütülmesi sırasında bir özel durumun oluşturulduğunu belirten bir işaret olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c826b-108">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="c826b-109">Bu durumda, özel durum sessizce yakalanacaktır ve yürütme COM çağıranına döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c826b-109">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c826b-110">Nedeni</span><span class="sxs-lookup"><span data-stu-id="c826b-110">Cause</span></span>  
 <span data-ttu-id="c826b-111">Bir özel durum oluşturuldu, ancak bunu raporlamak için geçerli bir yol yok.</span><span class="sxs-lookup"><span data-stu-id="c826b-111">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c826b-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="c826b-112">Resolution</span></span>  
 <span data-ttu-id="c826b-113">Yalnızca bilgilendirme, bir hatanın göstergesi olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c826b-113">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c826b-114">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="c826b-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="c826b-115">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c826b-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="c826b-116">Yalnızca sessizce yakalanan özel durumlarla ilgili verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="c826b-116">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c826b-117">Çıktı</span><span class="sxs-lookup"><span data-stu-id="c826b-117">Output</span></span>  
 <span data-ttu-id="c826b-118">Yöntem adı, tür adı ve özel durum iletisi içeren bilgilendirici ileti.</span><span class="sxs-lookup"><span data-stu-id="c826b-118">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c826b-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c826b-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c826b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c826b-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c826b-121">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="c826b-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c826b-122">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="c826b-122">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
