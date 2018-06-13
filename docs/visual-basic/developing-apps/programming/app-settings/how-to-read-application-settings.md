---
title: "Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma"
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 3de6e59c2a69c430a0376ef36f8ce52e57f5f6f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585687"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="40a21-102">Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma</span><span class="sxs-lookup"><span data-stu-id="40a21-102">How to: Read Application Settings in Visual Basic</span></span>
<span data-ttu-id="40a21-103">Bir kullanıcı ayarı üzerinde ayarın özelliğine erişerek okuyabilirsiniz `My.Settings` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="40a21-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="40a21-104">`My.Settings` Nesne her ayar özelliği olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="40a21-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="40a21-105">Özellik adı ayar adı ile aynıdır ve özellik türü ayar türü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="40a21-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="40a21-106">Ayarın **kapsam** özelliği salt okunur; olup olmadığını gösteren özelliği için bir **uygulama** kapsam ayarıdır hatayla özelliği için salt okunur bir **kullanıcı** kapsam ayarı okuma-yazma olur.</span><span class="sxs-lookup"><span data-stu-id="40a21-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="40a21-107">Daha fazla bilgi için bkz: [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="40a21-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="40a21-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="40a21-108">Example</span></span>  
 <span data-ttu-id="40a21-109">Bu örnek değerini görüntüler `Nickname` ayarı.</span><span class="sxs-lookup"><span data-stu-id="40a21-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 <span data-ttu-id="40a21-110">Bu örnekte çalışması, uygulamanızın olmalıdır bir `Nickname` türü ayarı `String`.</span><span class="sxs-lookup"><span data-stu-id="40a21-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="40a21-111">Daha fazla bilgi için bkz: [yönetme uygulama ayarları (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="40a21-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40a21-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40a21-112">See Also</span></span>  
 [<span data-ttu-id="40a21-113">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="40a21-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="40a21-114">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="40a21-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="40a21-115">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını sürdürmek</span><span class="sxs-lookup"><span data-stu-id="40a21-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="40a21-116">Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzları oluşturma</span><span class="sxs-lookup"><span data-stu-id="40a21-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [<span data-ttu-id="40a21-117">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="40a21-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
