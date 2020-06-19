---
title: My.Forms ve My.WebServices ile Sağlanan Varsayılan Nesne Örnekleri
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 141f2f5f98499498d3c6732f7ae8d0abe6259ed9
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990251"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="0928f-102">My.Forms ve My.WebServices ile Sağlanan Varsayılan Nesne Örnekleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0928f-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>

<span data-ttu-id="0928f-103">[My. Forms](../../language-reference/objects/my-forms-object.md) ve [My. WebServices](../../language-reference/objects/my-webservices-object.md) nesneleri, uygulamanız tarafından kullanılan formlara, veri kaynaklarına ve XML Web hizmetlerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="0928f-103">The [My.Forms](../../language-reference/objects/my-forms-object.md) and [My.WebServices](../../language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="0928f-104">Bunlar, bu nesnelerin her birinin *varsayılan örneklerinin* koleksiyonları aracılığıyla erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="0928f-104">They provide access through collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="0928f-105">Varsayılan örnekler</span><span class="sxs-lookup"><span data-stu-id="0928f-105">Default Instances</span></span>  

 <span data-ttu-id="0928f-106">Varsayılan örnek, çalışma zamanı tarafından sağlanmış bir sınıfının örneğidir ve ve deyimleri kullanılarak bildirilmesine ve örneklendirilmemelidir `Dim` `New` .</span><span class="sxs-lookup"><span data-stu-id="0928f-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="0928f-107">Aşağıdaki örnek, adlı bir sınıfın örneğini nasıl bildirdiğini ve örnekleyeceğinizi <xref:System.Windows.Forms.Form> `Form1` ve bundan böyle bu sınıfın varsayılan bir örneğini nasıl sağlayabileceğinizi gösterir <xref:System.Windows.Forms.Form> `My.Forms` .</span><span class="sxs-lookup"><span data-stu-id="0928f-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 <span data-ttu-id="0928f-108">`My.Forms`Nesnesi, projenizde bulunan her sınıf için bir varsayılan örnekler koleksiyonu döndürür `Form` .</span><span class="sxs-lookup"><span data-stu-id="0928f-108">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="0928f-109">Benzer şekilde, `My.WebServices` uygulamanızda bir başvuru oluşturduğunuz her Web hizmeti için proxy sınıfının varsayılan bir örneğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0928f-109">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0928f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0928f-110">See also</span></span>

- [<span data-ttu-id="0928f-111">My.Forms Nesnesi</span><span class="sxs-lookup"><span data-stu-id="0928f-111">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="0928f-112">My.WebServices Nesnesi</span><span class="sxs-lookup"><span data-stu-id="0928f-112">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="0928f-113">My Özellikleri Proje Türüne Nasıl Bağımlıdır</span><span class="sxs-lookup"><span data-stu-id="0928f-113">How My Depends on Project Type</span></span>](how-my-depends-on-project-type.md)
