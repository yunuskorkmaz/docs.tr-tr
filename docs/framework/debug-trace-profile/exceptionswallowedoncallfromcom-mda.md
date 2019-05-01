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
ms.openlocfilehash: 4f076cbc556c7d9feff8a226f050743cd7728622
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61874451"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="82f47-102">exceptionSwallowedOnCallFromCom MDA</span><span class="sxs-lookup"><span data-stu-id="82f47-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="82f47-103">`exceptionSwallowedOnCallFromCOM` Yönetilen hata ayıklama Yardımcısı (MDA), bir özel durum COM'dan yönetilmeyen HRESULT dönüş türü olmayan bir yöntem adlı ortak dil çalışma zamanı (CLR) kodu oluşturulduğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="82f47-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="82f47-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="82f47-104">Symptoms</span></span>  
 <span data-ttu-id="82f47-105">Bir çağrıdan yönetilen bir bileşeni için COM ile FALSE veya 0 değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="82f47-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="82f47-106">Alternatif olarak, yöntemin dönüş türü void varsa olabilir herhangi bir gösterge metodu yürütülürken bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="82f47-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="82f47-107">Bu durumda, özel durumu sessizce yakalanır ve yürütme COM çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="82f47-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="82f47-108">Sebep</span><span class="sxs-lookup"><span data-stu-id="82f47-108">Cause</span></span>  
 <span data-ttu-id="82f47-109">Bir özel durum oluştu, ancak bunu bildirmek için geçerli bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="82f47-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="82f47-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="82f47-110">Resolution</span></span>  
 <span data-ttu-id="82f47-111">Bilgilendirici yalnızca, bir hatanın mutlaka gösterir.</span><span class="sxs-lookup"><span data-stu-id="82f47-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="82f47-112">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="82f47-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="82f47-113">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="82f47-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="82f47-114">Yalnızca veri sessizce Yakalanan özel durumlar hakkında raporlar.</span><span class="sxs-lookup"><span data-stu-id="82f47-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="82f47-115">Çıkış</span><span class="sxs-lookup"><span data-stu-id="82f47-115">Output</span></span>  
 <span data-ttu-id="82f47-116">Yöntem adı, tür adı ve özel durum iletisi içeren bilgilendirme iletisi.</span><span class="sxs-lookup"><span data-stu-id="82f47-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="82f47-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="82f47-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="82f47-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82f47-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="82f47-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="82f47-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="82f47-120">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="82f47-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
