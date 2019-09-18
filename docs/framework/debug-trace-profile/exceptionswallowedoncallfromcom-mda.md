---
title: exceptionSwallowedOnCallFromCom MDA
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3a49bdce78c1445cd25de8755ded0f27a4902937
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052811"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="1bf45-102">exceptionSwallowedOnCallFromCom MDA</span><span class="sxs-lookup"><span data-stu-id="1bf45-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="1bf45-103">Yönetilen `exceptionSwallowedOnCallFromCOM` hata ayıklama Yardımcısı (MDA), yönetilmeyen bir HRESULT dönüş türüne sahip olmayan bir yöntem aracılığıyla com 'dan çağrılan ortak dil çalışma zamanı (CLR) kodundan bir özel durum oluştuğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1bf45-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1bf45-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="1bf45-104">Symptoms</span></span>  
 <span data-ttu-id="1bf45-105">COM 'tan yönetilen bileşen çağrısı, FALSE veya 0 değeri ile döndürür.</span><span class="sxs-lookup"><span data-stu-id="1bf45-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="1bf45-106">Alternatif olarak, yöntemin bir void dönüş türü varsa, yöntemin yürütülmesi sırasında bir özel durumun oluşturulduğunu belirten bir işaret olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1bf45-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="1bf45-107">Bu durumda, özel durum sessizce yakalanacaktır ve yürütme COM çağıranına döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1bf45-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1bf45-108">Sebep</span><span class="sxs-lookup"><span data-stu-id="1bf45-108">Cause</span></span>  
 <span data-ttu-id="1bf45-109">Bir özel durum oluşturuldu, ancak bunu raporlamak için geçerli bir yol yok.</span><span class="sxs-lookup"><span data-stu-id="1bf45-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1bf45-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="1bf45-110">Resolution</span></span>  
 <span data-ttu-id="1bf45-111">Yalnızca bilgilendirme, bir hatanın göstergesi olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1bf45-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1bf45-112">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="1bf45-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="1bf45-113">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1bf45-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="1bf45-114">Yalnızca sessizce yakalanan özel durumlarla ilgili verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="1bf45-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1bf45-115">Çıkış</span><span class="sxs-lookup"><span data-stu-id="1bf45-115">Output</span></span>  
 <span data-ttu-id="1bf45-116">Yöntem adı, tür adı ve özel durum iletisi içeren bilgilendirici ileti.</span><span class="sxs-lookup"><span data-stu-id="1bf45-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1bf45-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1bf45-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bf45-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bf45-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1bf45-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="1bf45-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1bf45-120">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="1bf45-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
