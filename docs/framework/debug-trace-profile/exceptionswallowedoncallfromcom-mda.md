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
ms.openlocfilehash: 4ccb03c9a8a473c10f15b00e64810b04f21504c9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217519"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="07586-102">exceptionSwallowedOnCallFromCom MDA</span><span class="sxs-lookup"><span data-stu-id="07586-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="07586-103">`exceptionSwallowedOnCallFromCOM` yönetilen hata ayıklama Yardımcısı (MDA), yönetilmeyen bir HRESULT dönüş türüne sahip olmayan bir yöntem aracılığıyla COM 'dan çağrılan ortak dil çalışma zamanı (CLR) kodundan bir özel durum oluştuğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="07586-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="07586-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="07586-104">Symptoms</span></span>  
 <span data-ttu-id="07586-105">COM 'tan yönetilen bileşen çağrısı, FALSE veya 0 değeri ile döndürür.</span><span class="sxs-lookup"><span data-stu-id="07586-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="07586-106">Alternatif olarak, yöntemin bir void dönüş türü varsa, yöntemin yürütülmesi sırasında bir özel durumun oluşturulduğunu belirten bir işaret olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="07586-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="07586-107">Bu durumda, özel durum sessizce yakalanacaktır ve yürütme COM çağıranına döndürülür.</span><span class="sxs-lookup"><span data-stu-id="07586-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="07586-108">Nedeni</span><span class="sxs-lookup"><span data-stu-id="07586-108">Cause</span></span>  
 <span data-ttu-id="07586-109">Bir özel durum oluşturuldu, ancak bunu raporlamak için geçerli bir yol yok.</span><span class="sxs-lookup"><span data-stu-id="07586-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="07586-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="07586-110">Resolution</span></span>  
 <span data-ttu-id="07586-111">Yalnızca bilgilendirme, bir hatanın göstergesi olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="07586-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="07586-112">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="07586-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="07586-113">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="07586-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="07586-114">Yalnızca sessizce yakalanan özel durumlarla ilgili verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="07586-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="07586-115">Çıktı</span><span class="sxs-lookup"><span data-stu-id="07586-115">Output</span></span>  
 <span data-ttu-id="07586-116">Yöntem adı, tür adı ve özel durum iletisi içeren bilgilendirici ileti.</span><span class="sxs-lookup"><span data-stu-id="07586-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="07586-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="07586-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="07586-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07586-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="07586-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="07586-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="07586-120">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="07586-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
