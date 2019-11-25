---
title: 'How to: Change User Settings'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: d24b6d239c894788ce67b0723b4bf034050bf307
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329623"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="318d6-102">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="318d6-102">How to: Change User Settings in Visual Basic</span></span>

<span data-ttu-id="318d6-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span><span class="sxs-lookup"><span data-stu-id="318d6-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="318d6-104">The `My.Settings` object exposes each setting as a property.</span><span class="sxs-lookup"><span data-stu-id="318d6-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="318d6-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span><span class="sxs-lookup"><span data-stu-id="318d6-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="318d6-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span><span class="sxs-lookup"><span data-stu-id="318d6-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="318d6-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="318d6-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="318d6-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span><span class="sxs-lookup"><span data-stu-id="318d6-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="318d6-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span><span class="sxs-lookup"><span data-stu-id="318d6-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="318d6-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="318d6-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="318d6-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="318d6-111">Example</span></span>  

 <span data-ttu-id="318d6-112">This example changes the value of the `Nickname` user setting.</span><span class="sxs-lookup"><span data-stu-id="318d6-112">This example changes the value of the `Nickname` user setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 <span data-ttu-id="318d6-113">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span><span class="sxs-lookup"><span data-stu-id="318d6-113">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="318d6-114">The application saves the user settings when the application shuts down.</span><span class="sxs-lookup"><span data-stu-id="318d6-114">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="318d6-115">To save the settings immediately, call the `My.Settings.Save` method.</span><span class="sxs-lookup"><span data-stu-id="318d6-115">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="318d6-116">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="318d6-116">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="318d6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="318d6-117">See also</span></span>

- [<span data-ttu-id="318d6-118">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="318d6-118">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="318d6-119">How to: Read Application Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="318d6-119">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="318d6-120">How to: Persist User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="318d6-120">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="318d6-121">How to: Create Property Grids for User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="318d6-121">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="318d6-122">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="318d6-122">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
