---
title: invalidMemberDeclaration MDA
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe15d718a9c5f91bfae4f37c04e726990e2fbd45
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052579"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="996f2-102">invalidMemberDeclaration MDA</span><span class="sxs-lookup"><span data-stu-id="996f2-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="996f2-103">Yönetilen `invalidMemberDeclaration` hata ayıklama Yardımcısı (MDA), com 'dan çağrılacak bir üyenin parametrelerinin nasıl hazırlanacağını belirlerken oluşan bir hatayı raporlamak için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="996f2-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="996f2-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="996f2-104">Symptoms</span></span>  
 <span data-ttu-id="996f2-105">Yönetilen yöntem çağrılmadan COM 'a bir hata HRESULT döndürülür.</span><span class="sxs-lookup"><span data-stu-id="996f2-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="996f2-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="996f2-106">Cause</span></span>  
 <span data-ttu-id="996f2-107">Bunun nedeni büyük olasılıkla parametrelerden birindeki uyumsuz <xref:System.Runtime.InteropServices.MarshalAsAttribute> bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="996f2-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="996f2-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="996f2-108">Resolution</span></span>  
 <span data-ttu-id="996f2-109">Parametrelerde geçerli <xref:System.Runtime.InteropServices.MarshalAsAttribute> öznitelikleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="996f2-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="996f2-110">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="996f2-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="996f2-111">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="996f2-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="996f2-112">Çıkış</span><span class="sxs-lookup"><span data-stu-id="996f2-112">Output</span></span>  
 <span data-ttu-id="996f2-113">Üye adı, tür adı ve hata iletisi içeren bilgilendirici bir ileti.</span><span class="sxs-lookup"><span data-stu-id="996f2-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="996f2-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="996f2-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="996f2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="996f2-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="996f2-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="996f2-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="996f2-117">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="996f2-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
