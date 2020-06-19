---
title: My.Resources ve My.Settings ile Hızlı Uygulama Geliştirme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: fd1ec25582e919b84235502f5921edfbc6e1dade
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990205"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="ff59d-102">My.Resources ve My.Settings ile Hızlı Uygulama Geliştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff59d-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>

<span data-ttu-id="ff59d-103">`My.Resources`Nesnesi, uygulamanın kaynaklarına erişim sağlar ve uygulamanıza yönelik kaynakları dinamik olarak almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff59d-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="ff59d-104">Kaynakları Alma</span><span class="sxs-lookup"><span data-stu-id="ff59d-104">Retrieving Resources</span></span>  

 <span data-ttu-id="ff59d-105">Ses dosyaları, simgeler, görüntüler ve dizeler gibi birçok kaynak nesne aracılığıyla alınabilir `My.Resources` .</span><span class="sxs-lookup"><span data-stu-id="ff59d-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="ff59d-106">Örneğin, uygulamanın kültüre özgü kaynak dosyalarına erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff59d-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="ff59d-107">Aşağıdaki örnek, formun simgesini `Form1Icon` uygulamanın kaynak dosyasında saklanan adlı simgeye ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ff59d-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 <span data-ttu-id="ff59d-108">`My.Resources`Nesne yalnızca genel kaynakları kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="ff59d-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="ff59d-109">Formlarla ilişkili kaynak dosyalarına erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="ff59d-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="ff59d-110">Form kaynaklarını formdan erişin.</span><span class="sxs-lookup"><span data-stu-id="ff59d-110">Access the form resources from the form.</span></span>  
  
 <span data-ttu-id="ff59d-111">Benzer şekilde, `My.Settings` nesnesi uygulamanın ayarlarına erişim sağlar ve uygulamanızın özellik ayarlarını ve diğer bilgilerini dinamik olarak depolamanızı ve almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff59d-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="ff59d-112">Daha fazla bilgi için bkz [. My. Resources nesnesi](../../language-reference/objects/my-resources-object.md) ve [My. Settings nesnesi](../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="ff59d-112">For more information, see [My.Resources Object](../../language-reference/objects/my-resources-object.md) and [My.Settings Object](../../language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff59d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff59d-113">See also</span></span>

- [<span data-ttu-id="ff59d-114">My.Resources Nesnesi</span><span class="sxs-lookup"><span data-stu-id="ff59d-114">My.Resources Object</span></span>](../../language-reference/objects/my-resources-object.md)
- [<span data-ttu-id="ff59d-115">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="ff59d-115">My.Settings Object</span></span>](../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="ff59d-116">Uygulama Ayarlarına Erişme</span><span class="sxs-lookup"><span data-stu-id="ff59d-116">Accessing Application Settings</span></span>](../programming/app-settings/index.md)
