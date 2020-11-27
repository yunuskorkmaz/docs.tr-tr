---
title: invalidMemberDeclaration MDA
description: Yönetilen yöntemi çağırmadan COM 'a bir hata HRESULT döndürülürse çağrılan ınvalidmemberdeclaration yönetilen hata ayıklama Yardımcısı ' nı gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
ms.openlocfilehash: c8d6c69fc6eb4f5f690b02809fdc492da675c3b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272559"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="b50a3-103">invalidMemberDeclaration MDA</span><span class="sxs-lookup"><span data-stu-id="b50a3-103">invalidMemberDeclaration MDA</span></span>

<span data-ttu-id="b50a3-104">`invalidMemberDeclaration`Yönetilen hata ayıklama Yardımcısı (MDA), com 'dan çağrılacak bir üyenin parametrelerinin nasıl hazırlanacağını belirlerken oluşan bir hatayı raporlamak için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b50a3-104">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b50a3-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="b50a3-105">Symptoms</span></span>  

 <span data-ttu-id="b50a3-106">Yönetilen yöntem çağrılmadan COM 'a bir hata HRESULT döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b50a3-106">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b50a3-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="b50a3-107">Cause</span></span>  

 <span data-ttu-id="b50a3-108">Bunun nedeni büyük olasılıkla parametrelerden birindeki uyumsuz bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="b50a3-108">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b50a3-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="b50a3-109">Resolution</span></span>  

 <span data-ttu-id="b50a3-110">Parametrelerde geçerli <xref:System.Runtime.InteropServices.MarshalAsAttribute> öznitelikleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="b50a3-110">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b50a3-111">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="b50a3-111">Effect on the Runtime</span></span>  

 <span data-ttu-id="b50a3-112">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b50a3-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b50a3-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="b50a3-113">Output</span></span>  

 <span data-ttu-id="b50a3-114">Üye adı, tür adı ve hata iletisi içeren bilgilendirici bir ileti.</span><span class="sxs-lookup"><span data-stu-id="b50a3-114">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b50a3-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b50a3-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b50a3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b50a3-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="b50a3-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="b50a3-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="b50a3-118">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="b50a3-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
