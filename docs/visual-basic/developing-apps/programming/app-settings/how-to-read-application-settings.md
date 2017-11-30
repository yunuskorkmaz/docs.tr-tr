---
title: "Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea6cfc529262053daf7c8111271de2c51e9cab4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="8408a-102">Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma</span><span class="sxs-lookup"><span data-stu-id="8408a-102">How to: Read Application Settings in Visual Basic</span></span>
<span data-ttu-id="8408a-103">Bir kullanıcı ayarı üzerinde ayarın özelliğine erişerek okuyabilirsiniz `My.Settings` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="8408a-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="8408a-104">`My.Settings` Nesne her ayar özelliği olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="8408a-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="8408a-105">Özellik adı ayar adı ile aynıdır ve özellik türü ayar türü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="8408a-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="8408a-106">Ayarın **kapsam** özelliği salt okunur; olup olmadığını gösteren özelliği için bir **uygulama** kapsam ayarıdır hatayla özelliği için salt okunur bir **kullanıcı** kapsam ayarı okuma-yazma olur.</span><span class="sxs-lookup"><span data-stu-id="8408a-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="8408a-107">Daha fazla bilgi için bkz: [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="8408a-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8408a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="8408a-108">Example</span></span>  
 <span data-ttu-id="8408a-109">Bu örnek değerini görüntüler `Nickname` ayarı.</span><span class="sxs-lookup"><span data-stu-id="8408a-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 <span data-ttu-id="8408a-110">Bu örnekte çalışması, uygulamanızın olmalıdır bir `Nickname` türü ayarı `String`.</span><span class="sxs-lookup"><span data-stu-id="8408a-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="8408a-111">Daha fazla bilgi için bkz: [yönetme uygulama ayarları (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="8408a-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8408a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8408a-112">See Also</span></span>  
 [<span data-ttu-id="8408a-113">My.Settings nesnesi</span><span class="sxs-lookup"><span data-stu-id="8408a-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="8408a-114">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="8408a-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="8408a-115">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını sürdürmek</span><span class="sxs-lookup"><span data-stu-id="8408a-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="8408a-116">Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzları oluşturma</span><span class="sxs-lookup"><span data-stu-id="8408a-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [<span data-ttu-id="8408a-117">Uygulama ayarları (.NET) yönetme</span><span class="sxs-lookup"><span data-stu-id="8408a-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
