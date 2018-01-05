---
title: "My.Resources ve My.Settings ile Hızlı Uygulama Geliştirme (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7339afdc35341739b592b2a327094754031c346c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="9190a-102">My.Resources ve My.Settings ile Hızlı Uygulama Geliştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9190a-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>
<span data-ttu-id="9190a-103">`My.Resources` Nesne uygulamanın kaynaklarına erişmesini sağlar ve uygulamanız için kaynakları dinamik olarak almanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9190a-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="9190a-104">Kaynakları Alma</span><span class="sxs-lookup"><span data-stu-id="9190a-104">Retrieving Resources</span></span>  
 <span data-ttu-id="9190a-105">Ses dosyalarını, simgeler, görüntüler ve dizeler gibi kaynakları çeşitli alınabilir `My.Resources` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9190a-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="9190a-106">Örneğin, uygulamanın kültüre özgü kaynak dosyalara erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9190a-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="9190a-107">Aşağıdaki örnek form simgesini adlı simgesi ayarlar `Form1Icon` uygulamanın kaynak dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="9190a-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 <span data-ttu-id="9190a-108">`My.Resources` Nesne yalnızca Genel kaynaklar kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="9190a-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="9190a-109">Formları ile ilişkili kaynak dosyalarına erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="9190a-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="9190a-110">Form kaynaklarını formdan erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9190a-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="9190a-111">Benzer şekilde, `My.Settings` nesne uygulamanın ayarlarına erişim sağlar ve dinamik olarak depolamak ve özellik ayarları ve uygulamanız için diğer bilgilerini almak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9190a-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="9190a-112">Daha fazla bilgi için bkz: [My.Resources nesnesi](../../../visual-basic/language-reference/objects/my-resources-object.md) ve [My.Settings nesnesi](../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="9190a-112">For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9190a-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9190a-113">See Also</span></span>  
 [<span data-ttu-id="9190a-114">My.Resources Nesnesi</span><span class="sxs-lookup"><span data-stu-id="9190a-114">My.Resources Object</span></span>](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [<span data-ttu-id="9190a-115">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="9190a-115">My.Settings Object</span></span>](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="9190a-116">Uygulama Ayarlarına Erişme</span><span class="sxs-lookup"><span data-stu-id="9190a-116">Accessing Application Settings</span></span>](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
