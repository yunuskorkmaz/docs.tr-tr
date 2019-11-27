---
title: 'Nasıl yapılır: uygulama ayarlarını okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 04726381f8d285ae61045d1624b3b41b7f47e491
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329565"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="9deb7-102">Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma</span><span class="sxs-lookup"><span data-stu-id="9deb7-102">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="9deb7-103">`My.Settings` nesnesindeki ayar özelliğine erişerek bir kullanıcı ayarını okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9deb7-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="9deb7-104">`My.Settings` nesnesi her ayarı bir özellik olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="9deb7-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="9deb7-105">Özellik adı, ayar adıyla aynıdır ve özellik türü ayar türüyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9deb7-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="9deb7-106">Ayarın **kapsamı** , özelliğin salt okunurdur belirtir; bir **uygulama** kapsamı ayarının özelliği salt okunurdur, ancak bir **Kullanıcı** kapsamı ayarı özelliği okuma-yazma olur.</span><span class="sxs-lookup"><span data-stu-id="9deb7-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="9deb7-107">Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="9deb7-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9deb7-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="9deb7-108">Example</span></span>  

 <span data-ttu-id="9deb7-109">Bu örnek `Nickname` ayarının değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9deb7-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="9deb7-110">Bu örneğin çalışması için, uygulamanızın `String`türünde bir `Nickname` ayarı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9deb7-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="9deb7-111">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="9deb7-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9deb7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9deb7-112">See also</span></span>

- [<span data-ttu-id="9deb7-113">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="9deb7-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="9deb7-114">Nasıl yapılır: Visual Basic Kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="9deb7-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="9deb7-115">Nasıl yapılır: Visual Basic 'de Kullanıcı ayarlarını kalıcı hale getirme</span><span class="sxs-lookup"><span data-stu-id="9deb7-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="9deb7-116">Nasıl yapılır: Visual Basic Kullanıcı ayarları için özellik kılavuzları oluşturma</span><span class="sxs-lookup"><span data-stu-id="9deb7-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="9deb7-117">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="9deb7-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
