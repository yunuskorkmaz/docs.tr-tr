---
title: invalidMemberDeclaration MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71313a14ba1f9222e19dbf9f8180280d0e8c444d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="a3159-102">invalidMemberDeclaration MDA</span><span class="sxs-lookup"><span data-stu-id="a3159-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="a3159-103">`invalidMemberDeclaration` Yönetilen hata ayıklama Yardımcısı (MDA) nasıl hazırlanacağını COM'dan çağrılacak üye parametrelerinin belirlenirken oluşan bir hatayı bildirmek için etkinleştirildi</span><span class="sxs-lookup"><span data-stu-id="a3159-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a3159-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="a3159-104">Symptoms</span></span>  
 <span data-ttu-id="a3159-105">Bir hata, yönetilen yöntemi olarak adlandırılan COM HRESULT döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a3159-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a3159-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="a3159-106">Cause</span></span>  
 <span data-ttu-id="a3159-107">Bu uyumsuz nedeniyle büyük olasılıkla <xref:System.Runtime.InteropServices.MarshalAsAttribute> parametrelerden biri özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a3159-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a3159-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="a3159-108">Resolution</span></span>  
 <span data-ttu-id="a3159-109">Geçerli belirtin <xref:System.Runtime.InteropServices.MarshalAsAttribute> parametreleri öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="a3159-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a3159-110">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="a3159-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="a3159-111">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a3159-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a3159-112">Çıkış</span><span class="sxs-lookup"><span data-stu-id="a3159-112">Output</span></span>  
 <span data-ttu-id="a3159-113">Üye adı, türü adı ve hata iletisi içeren bir bilgi iletisidir.</span><span class="sxs-lookup"><span data-stu-id="a3159-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a3159-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a3159-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3159-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a3159-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="a3159-116">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="a3159-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="a3159-117">Birlikte çalışma hazırlama</span><span class="sxs-lookup"><span data-stu-id="a3159-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
