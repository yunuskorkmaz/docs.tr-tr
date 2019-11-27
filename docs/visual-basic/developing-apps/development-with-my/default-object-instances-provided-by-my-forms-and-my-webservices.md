---
title: My.Forms ve My.WebServices ile Sağlanan Varsayılan Nesne Örnekleri
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: d06df4bd023892429b2aaefdd624398a6546d06d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330212"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="39458-102">My.Forms ve My.WebServices ile Sağlanan Varsayılan Nesne Örnekleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39458-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>

<span data-ttu-id="39458-103">[My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) ve [My. WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) nesneleri, uygulamanız tarafından kullanılan formlara, veri kaynaklarına ve XML Web hizmetlerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="39458-103">The [My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) and [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="39458-104">Bu nesneleri, bu nesnelerin her birinin *varsayılan örnek* koleksiyonlarını sunarak yapabilirler.</span><span class="sxs-lookup"><span data-stu-id="39458-104">They do this by providing collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="39458-105">Varsayılan örnekler</span><span class="sxs-lookup"><span data-stu-id="39458-105">Default Instances</span></span>  

 <span data-ttu-id="39458-106">Varsayılan örnek, çalışma zamanı tarafından sağlanmış bir sınıfının örneğidir ve `Dim` ve `New` deyimleri kullanılarak bildirilmesine ve örneklendirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="39458-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="39458-107">Aşağıdaki örnek, `Form1`adlı bir <xref:System.Windows.Forms.Form> sınıfın örneğini nasıl bildirdiğini ve örnekleyeceğinizi ve `My.Forms`aracılığıyla bu <xref:System.Windows.Forms.Form> sınıfının varsayılan bir örneğini nasıl sağlayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="39458-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 <span data-ttu-id="39458-108">`My.Forms` nesnesi, projenizde bulunan her `Form` sınıfının varsayılan örneklerinin bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="39458-108">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="39458-109">Benzer şekilde, `My.WebServices` uygulamanızda bir başvuru oluşturduğunuz her Web hizmeti için proxy sınıfının varsayılan bir örneğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="39458-109">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39458-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39458-110">See also</span></span>

- [<span data-ttu-id="39458-111">My.Forms Nesnesi</span><span class="sxs-lookup"><span data-stu-id="39458-111">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="39458-112">My.WebServices Nesnesi</span><span class="sxs-lookup"><span data-stu-id="39458-112">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="39458-113">My Özellikleri Proje Türüne Nasıl Bağımlıdır</span><span class="sxs-lookup"><span data-stu-id="39458-113">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
