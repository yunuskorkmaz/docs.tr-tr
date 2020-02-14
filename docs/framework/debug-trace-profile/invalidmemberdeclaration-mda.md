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
ms.openlocfilehash: 6033cd4178b2bc493794b5dcc527bc543ba24284
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216291"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="63d29-102">invalidMemberDeclaration MDA</span><span class="sxs-lookup"><span data-stu-id="63d29-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="63d29-103">`invalidMemberDeclaration` yönetilen hata ayıklama Yardımcısı (MDA), COM 'dan çağrılacak bir üyenin parametrelerinin nasıl hazırlanacağını belirlerken oluşan bir hatayı raporlamak için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="63d29-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="63d29-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="63d29-104">Symptoms</span></span>  
 <span data-ttu-id="63d29-105">Yönetilen yöntem çağrılmadan COM 'a bir hata HRESULT döndürülür.</span><span class="sxs-lookup"><span data-stu-id="63d29-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="63d29-106">Nedeni</span><span class="sxs-lookup"><span data-stu-id="63d29-106">Cause</span></span>  
 <span data-ttu-id="63d29-107">Bunun nedeni, parametrelerden birindeki uyumsuz bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="63d29-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="63d29-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="63d29-108">Resolution</span></span>  
 <span data-ttu-id="63d29-109">Parametrelerde geçerli <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliklerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="63d29-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="63d29-110">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="63d29-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="63d29-111">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="63d29-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="63d29-112">Çıktı</span><span class="sxs-lookup"><span data-stu-id="63d29-112">Output</span></span>  
 <span data-ttu-id="63d29-113">Üye adı, tür adı ve hata iletisi içeren bilgilendirici bir ileti.</span><span class="sxs-lookup"><span data-stu-id="63d29-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="63d29-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="63d29-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="63d29-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63d29-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="63d29-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="63d29-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="63d29-117">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="63d29-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
