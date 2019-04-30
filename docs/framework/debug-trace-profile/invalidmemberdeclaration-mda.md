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
ms.openlocfilehash: 4e5b4cb4a04a79a748f4ea2292bac67a88a6e9f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754368"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="4bb81-102">invalidMemberDeclaration MDA</span><span class="sxs-lookup"><span data-stu-id="4bb81-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="4bb81-103">`invalidMemberDeclaration` Yönetilen hata ayıklama Yardımcısı (MDA) nasıl hazırlanacağını COM'dan çağrılacak üye parametrelerinin belirlenirken oluşan bir hatayı raporlamak için etkinleştirildi</span><span class="sxs-lookup"><span data-stu-id="4bb81-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4bb81-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="4bb81-104">Symptoms</span></span>  
 <span data-ttu-id="4bb81-105">Bir hata HRESULT adlı Yönetilen yöntemi COM döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4bb81-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4bb81-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="4bb81-106">Cause</span></span>  
 <span data-ttu-id="4bb81-107">Uyumsuz bir nedeni büyük olasılıkla budur <xref:System.Runtime.InteropServices.MarshalAsAttribute> parametrelerden biri özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4bb81-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4bb81-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="4bb81-108">Resolution</span></span>  
 <span data-ttu-id="4bb81-109">Geçerli belirtin <xref:System.Runtime.InteropServices.MarshalAsAttribute> parametreleri öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="4bb81-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4bb81-110">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="4bb81-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="4bb81-111">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4bb81-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4bb81-112">Çıkış</span><span class="sxs-lookup"><span data-stu-id="4bb81-112">Output</span></span>  
 <span data-ttu-id="4bb81-113">Üye adı, tür adı ve hata iletisi içeren bir bilgi iletisidir.</span><span class="sxs-lookup"><span data-stu-id="4bb81-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4bb81-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4bb81-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4bb81-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bb81-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="4bb81-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="4bb81-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="4bb81-117">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="4bb81-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
