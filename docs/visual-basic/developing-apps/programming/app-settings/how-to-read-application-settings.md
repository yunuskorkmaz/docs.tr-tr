---
title: "Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma"
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: e7d909563ca7e991a51c2f921b5248aa587a83d7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823590"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="5c23b-102">Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma</span><span class="sxs-lookup"><span data-stu-id="5c23b-102">How to: Read Application Settings in Visual Basic</span></span>
<span data-ttu-id="5c23b-103">Bir kullanıcı ayarı üzerinde ayarın özelliğine erişerek edinebilirsiniz `My.Settings` nesne.</span><span class="sxs-lookup"><span data-stu-id="5c23b-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="5c23b-104">`My.Settings` Nesnesi, her ayarın bir özellik olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="5c23b-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="5c23b-105">Özellik adı ayar adı ile aynıdır ve özellik türü ayar türü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="5c23b-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="5c23b-106">Ayarın **kapsam** özelliği salt okunur; olup olmadığını gösterir özellik için bir **uygulama** kapsam ayardır sırasında özelliği salt okunur bir **kullanıcı** kapsam ayarı okunur-yazılır olmuştur.</span><span class="sxs-lookup"><span data-stu-id="5c23b-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="5c23b-107">Daha fazla bilgi için [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="5c23b-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c23b-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c23b-108">Example</span></span>  
 <span data-ttu-id="5c23b-109">Bu örnek değeri görüntüler `Nickname` ayarı.</span><span class="sxs-lookup"><span data-stu-id="5c23b-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="5c23b-110">Bu örneğin çalışması, uygulamanız olmalıdır bir `Nickname` biriminin türü `String`.</span><span class="sxs-lookup"><span data-stu-id="5c23b-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="5c23b-111">Daha fazla bilgi için [uygulama ayarlarını yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5c23b-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c23b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c23b-112">See also</span></span>

- [<span data-ttu-id="5c23b-113">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="5c23b-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="5c23b-114">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="5c23b-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="5c23b-115">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma</span><span class="sxs-lookup"><span data-stu-id="5c23b-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="5c23b-116">Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzu oluşturma</span><span class="sxs-lookup"><span data-stu-id="5c23b-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="5c23b-117">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="5c23b-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
