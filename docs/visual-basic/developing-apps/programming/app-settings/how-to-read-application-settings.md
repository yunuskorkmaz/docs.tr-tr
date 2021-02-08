---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic uygulama ayarlarını okuma'
title: 'Nasıl yapılır: Uygulama Ayarlarını Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 30b5a3b0cdf3565fc8c1f0dfa19e7717a714c350
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797828"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="e2f79-103">Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma</span><span class="sxs-lookup"><span data-stu-id="e2f79-103">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="e2f79-104">Nesne üzerindeki ayara erişerek bir kullanıcı ayarını okuyabilirsiniz `My.Settings` .</span><span class="sxs-lookup"><span data-stu-id="e2f79-104">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="e2f79-105">`My.Settings`Nesnesi her ayarı bir özellik olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2f79-105">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="e2f79-106">Özellik adı, ayar adıyla aynıdır ve özellik türü ayar türüyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e2f79-106">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="e2f79-107">Ayarın **kapsamı** , özelliğin salt okunurdur belirtir; bir **uygulama** kapsamı ayarının özelliği salt okunurdur, ancak bir **Kullanıcı** kapsamı ayarı özelliği okuma-yazma olur.</span><span class="sxs-lookup"><span data-stu-id="e2f79-107">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="e2f79-108">Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="e2f79-108">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2f79-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2f79-109">Example</span></span>  

 <span data-ttu-id="e2f79-110">Bu örnek, ayarın değerini gösterir `Nickname` .</span><span class="sxs-lookup"><span data-stu-id="e2f79-110">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="e2f79-111">Bu örneğin çalışması için, uygulamanızın türünde bir ayarı olması gerekir `Nickname` `String` .</span><span class="sxs-lookup"><span data-stu-id="e2f79-111">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="e2f79-112">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="e2f79-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f79-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2f79-113">See also</span></span>

- [<span data-ttu-id="e2f79-114">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="e2f79-114">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="e2f79-115">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="e2f79-115">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="e2f79-116">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma</span><span class="sxs-lookup"><span data-stu-id="e2f79-116">How to: Persist User Settings in Visual Basic</span></span>](how-to-persist-user-settings.md)
- [<span data-ttu-id="e2f79-117">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e2f79-117">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="e2f79-118">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="e2f79-118">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
