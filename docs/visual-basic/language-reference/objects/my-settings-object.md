---
title: My.Settings Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 9560a51332ea596d4cf2228f1e07c158a0457ece
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350354"
---
# <a name="mysettings-object"></a><span data-ttu-id="b6277-102">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="b6277-102">My.Settings Object</span></span>
<span data-ttu-id="b6277-103">Uygulamanın ayarlarına erişmek için özellikleri ve yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6277-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6277-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6277-104">Remarks</span></span>  
 <span data-ttu-id="b6277-105">`My.Settings` nesnesi uygulama ayarlarına erişim sağlar ve uygulamanızın özellik ayarlarını ve diğer bilgilerini dinamik olarak depolamanızı ve almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6277-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="b6277-106">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="b6277-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b6277-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b6277-107">Properties</span></span>  
 <span data-ttu-id="b6277-108">`My.Settings` nesnesinin özellikleri uygulamanızın ayarlarına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6277-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="b6277-109">Ayarları eklemek veya kaldırmak için, **Ayarlar tasarımcısını**kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6277-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="b6277-110">Her ayarın bir **adı**, **türü**, **kapsamı**ve **değeri**vardır ve bu ayarlar `My.Settings` nesnesinde her bir ayara erişme özelliğinin nasıl göründüğünü belirlenir:</span><span class="sxs-lookup"><span data-stu-id="b6277-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="b6277-111">**Ad** , özelliğin adını belirler.</span><span class="sxs-lookup"><span data-stu-id="b6277-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="b6277-112">**Tür** , özelliğin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="b6277-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="b6277-113">**Kapsam** , özelliğin salt okunurdur olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6277-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="b6277-114">Değer **uygulama**ise, özellik salt okunurdur; değer **Kullanıcı**ise, özelliği okuma-yazma olur.</span><span class="sxs-lookup"><span data-stu-id="b6277-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="b6277-115">**Değer** , özelliğin varsayılan değeridir.</span><span class="sxs-lookup"><span data-stu-id="b6277-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6277-116">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b6277-116">Methods</span></span>  
  
|<span data-ttu-id="b6277-117">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b6277-117">Method</span></span>|<span data-ttu-id="b6277-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6277-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="b6277-119">Son kaydedilen değerlerden Kullanıcı ayarlarını yeniden yükler.</span><span class="sxs-lookup"><span data-stu-id="b6277-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="b6277-120">Geçerli Kullanıcı ayarlarını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b6277-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="b6277-121">`My.Settings` nesnesi, <xref:System.Configuration.ApplicationSettingsBase> sınıfından devralınan gelişmiş özellikler ve yöntemler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6277-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="b6277-122">Görevler</span><span class="sxs-lookup"><span data-stu-id="b6277-122">Tasks</span></span>  
 <span data-ttu-id="b6277-123">Aşağıdaki tabloda `My.Settings` nesnesini içeren görevlerin örnekleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="b6277-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="b6277-124">Bitiş</span><span class="sxs-lookup"><span data-stu-id="b6277-124">To</span></span>|<span data-ttu-id="b6277-125">Bkz.</span><span class="sxs-lookup"><span data-stu-id="b6277-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="b6277-126">Uygulama ayarını oku</span><span class="sxs-lookup"><span data-stu-id="b6277-126">Read an application setting</span></span>|[<span data-ttu-id="b6277-127">Nasıl yapılır: Visual Basic uygulama ayarlarını okuma</span><span class="sxs-lookup"><span data-stu-id="b6277-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="b6277-128">Kullanıcı ayarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="b6277-128">Change a user setting</span></span>|[<span data-ttu-id="b6277-129">Nasıl yapılır: Visual Basic Kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="b6277-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="b6277-130">Kullanıcı ayarlarını kalıcı yap</span><span class="sxs-lookup"><span data-stu-id="b6277-130">Persist user settings</span></span>|[<span data-ttu-id="b6277-131">Nasıl yapılır: Visual Basic 'de Kullanıcı ayarlarını kalıcı hale getirme</span><span class="sxs-lookup"><span data-stu-id="b6277-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="b6277-132">Kullanıcı ayarları için özellik Kılavuzu oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6277-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="b6277-133">Nasıl yapılır: Visual Basic Kullanıcı ayarları için özellik kılavuzları oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6277-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="b6277-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="b6277-134">Example</span></span>  
 <span data-ttu-id="b6277-135">Bu örnek `Nickname` ayarının değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b6277-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="b6277-136">Bu örneğin çalışması için, uygulamanızın `String`türünde bir `Nickname` ayarı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6277-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6277-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6277-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="b6277-138">Nasıl yapılır: Visual Basic uygulama ayarlarını okuma</span><span class="sxs-lookup"><span data-stu-id="b6277-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="b6277-139">Nasıl yapılır: Visual Basic Kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="b6277-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="b6277-140">Nasıl yapılır: Visual Basic 'de Kullanıcı ayarlarını kalıcı hale getirme</span><span class="sxs-lookup"><span data-stu-id="b6277-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="b6277-141">Nasıl yapılır: Visual Basic Kullanıcı ayarları için özellik kılavuzları oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6277-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="b6277-142">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="b6277-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
