---
title: My.Forms ve My.WebServices ile Sağlanan Varsayılan Nesne Örnekleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: ca31e1c40c77bf7f42d246019d81f4ffaed646e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014459"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="dbc09-102">My.Forms ve My.WebServices ile Sağlanan Varsayılan Nesne Örnekleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbc09-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>
<span data-ttu-id="dbc09-103">[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) ve [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) nesneleri, forms, veri kaynakları ve uygulamanız tarafından kullanılan XML Web Hizmetleri erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbc09-103">The [My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) and [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="dbc09-104">Koleksiyonları sağlayarak bunu *varsayılan örnekleri* bu nesnelerin her biri.</span><span class="sxs-lookup"><span data-stu-id="dbc09-104">They do this by providing collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="dbc09-105">Varsayılan örnekleri</span><span class="sxs-lookup"><span data-stu-id="dbc09-105">Default Instances</span></span>  
 <span data-ttu-id="dbc09-106">Varsayılan bir örnek olması gerekmez ve çalışma zamanı tarafından sağlanan sınıfının bir örneği olduğu bildirildi ve örneği kullanarak `Dim` ve `New` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="dbc09-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="dbc09-107">Aşağıdaki örnek nasıl sahip olabileceğiniz bildirilmiş ve bir örneğini örneği gösterir. bir <xref:System.Windows.Forms.Form> adlı sınıf `Form1`, ve nasıl artık bu varsayılan örneğini almak <xref:System.Windows.Forms.Form> aracılığıyla sınıf `My.Forms`.</span><span class="sxs-lookup"><span data-stu-id="dbc09-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 <span data-ttu-id="dbc09-108">`My.Forms` Nesnesi için varsayılan örneklerinin bir koleksiyonunu döndürür her `Form` projenizde var. sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dbc09-108">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="dbc09-109">Benzer şekilde, `My.WebServices` uygulamanızda bir başvuru oluşturduğunuz her Web hizmeti proxy sınıfın varsayılan bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbc09-109">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc09-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbc09-110">See also</span></span>

- [<span data-ttu-id="dbc09-111">My.Forms Nesnesi</span><span class="sxs-lookup"><span data-stu-id="dbc09-111">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="dbc09-112">My.WebServices Nesnesi</span><span class="sxs-lookup"><span data-stu-id="dbc09-112">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="dbc09-113">My Özellikleri Proje Türüne Nasıl Bağımlıdır</span><span class="sxs-lookup"><span data-stu-id="dbc09-113">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
