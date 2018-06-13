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
ms.openlocfilehash: b4c1cbf075ef96073061679b6d062075490f5e4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390614"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="9dd5e-102">exceptionSwallowedOnCallFromCom MDA</span><span class="sxs-lookup"><span data-stu-id="9dd5e-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="9dd5e-103">`exceptionSwallowedOnCallFromCOM` Yönetilen hata ayıklama Yardımcısı (MDA) kodundan COM dönüş türü bir yönetilmeyen HRESULT sahip olmayan bir yöntem adlı ortak dil çalışma zamanı (CLR) bir özel durum oluştuğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9dd5e-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="9dd5e-104">Symptoms</span></span>  
 <span data-ttu-id="9dd5e-105">Yönetilen bir bileşen için bir arama COM bağlantısını FALSE veya 0 değerine sahip döndürür.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="9dd5e-106">Alternatif olarak, yöntemin dönüş türü void varsa, olabilir yönteminin yürütülmesi sırasında özel durum oluştu hiçbir belirti.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="9dd5e-107">Bu durumda, özel durum sessizce yakalanan ve yürütme COM çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9dd5e-108">Sebep</span><span class="sxs-lookup"><span data-stu-id="9dd5e-108">Cause</span></span>  
 <span data-ttu-id="9dd5e-109">Özel durum oluştu, ancak bunu bildirmek için geçerli bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9dd5e-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="9dd5e-110">Resolution</span></span>  
 <span data-ttu-id="9dd5e-111">Yalnızca, hatanın mutlaka hatırlanması bilgilendirici.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9dd5e-112">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="9dd5e-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="9dd5e-113">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="9dd5e-114">Yalnızca veri sessizce Yakalanan özel durumlar hakkında raporlar.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9dd5e-115">Çıkış</span><span class="sxs-lookup"><span data-stu-id="9dd5e-115">Output</span></span>  
 <span data-ttu-id="9dd5e-116">Yöntem adı, türü adı ve özel durum iletisi içeren bilgi iletisi.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9dd5e-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9dd5e-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9dd5e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9dd5e-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="9dd5e-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="9dd5e-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="9dd5e-120">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="9dd5e-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
