---
title: 'Nasıl Yapılır: Uygulama Ayarlarını Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 04726381f8d285ae61045d1624b3b41b7f47e491
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329565"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="d22db-102">Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma</span><span class="sxs-lookup"><span data-stu-id="d22db-102">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="d22db-103">Nesne üzerinde ayarın özelliğine erişerek bir kullanıcı `My.Settings` ayarını okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d22db-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="d22db-104">Nesne `My.Settings` her ayarı bir özellik olarak ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="d22db-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="d22db-105">Özellik adı ayar adı ile aynıdır ve özellik türü ayar türüyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d22db-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="d22db-106">Ayarın **Kapsamı** özelliğin salt okunup okunmaz olduğunu gösterir; **Bir Uygulama** kapsamı ayarı için özellik salt okunur, **Kullanıcı** kapsam ayarı için özellik okuma-yazma.</span><span class="sxs-lookup"><span data-stu-id="d22db-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="d22db-107">Daha fazla bilgi için [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)' e bakın.</span><span class="sxs-lookup"><span data-stu-id="d22db-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d22db-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d22db-108">Example</span></span>  

 <span data-ttu-id="d22db-109">Bu örnek, `Nickname` ayarın değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d22db-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="d22db-110">Bu örneğin çalışması için, uygulamanızın `Nickname` türünde `String`bir ayarı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d22db-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="d22db-111">Daha fazla bilgi için bkz: [Uygulama Ayarlarını Yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="d22db-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d22db-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d22db-112">See also</span></span>

- [<span data-ttu-id="d22db-113">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="d22db-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="d22db-114">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="d22db-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="d22db-115">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma</span><span class="sxs-lookup"><span data-stu-id="d22db-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="d22db-116">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d22db-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="d22db-117">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="d22db-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
