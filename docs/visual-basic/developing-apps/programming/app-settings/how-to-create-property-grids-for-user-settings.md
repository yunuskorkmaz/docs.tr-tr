---
title: "Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 81a79945dfc0b1501134bc1b0197c18093a5dfae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="f807e-102">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f807e-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>
<span data-ttu-id="f807e-103">Kullanıcı ayarları için özellik kılavuzunu doldurarak oluşturabileceğiniz bir <xref:System.Windows.Forms.PropertyGrid> kullanıcı ayarı özelliklerinin denetimiyle `My.Settings` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f807e-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f807e-104">Çalışmak bu örnek için uygulamanızın yapılandırılmış kullanıcı ayarlarını olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f807e-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="f807e-105">Daha fazla bilgi için bkz: [yönetme uygulama ayarları (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f807e-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="f807e-106">`My.Settings` Nesne her ayar özelliği olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="f807e-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="f807e-107">Özellik adı ayar adı ile aynıdır ve özellik türü ayar türü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f807e-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="f807e-108">Ayarın **kapsam** özelliği salt okunur; olup olmadığını belirler özelliği için bir **uygulama**-kapsam ayarıdır hatayla özelliği için salt okunur bir **kullanıcı**-kapsamı salt okunur bir ayardır.</span><span class="sxs-lookup"><span data-stu-id="f807e-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="f807e-109">Daha fazla bilgi için bkz: [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="f807e-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f807e-110">Değiştiremez veya çalışma zamanında uygulama kapsamı ayarlarının değerleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f807e-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="f807e-111">Uygulama kapsam ayarları değiştirilebilir, yalnızca uygulama oluşturulurken (aracılığıyla **Proje Tasarımcısı**) ya da uygulamanın yapılandırma dosyasını düzenleyerek.</span><span class="sxs-lookup"><span data-stu-id="f807e-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="f807e-112">Daha fazla bilgi için bkz: [yönetme uygulama ayarları (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f807e-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="f807e-113">Bu örnekte bir <xref:System.Windows.Forms.PropertyGrid> kullanıcı ayarı özelliklerine erişmek için Denetim `My.Settings` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f807e-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="f807e-114">Varsayılan olarak, <xref:System.Windows.Forms.PropertyGrid> tüm özelliklerini gösterir `My.Settings` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f807e-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="f807e-115">Ancak, kullanıcı ayarı özelliklerine sahip <xref:System.Configuration.UserScopedSettingAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f807e-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="f807e-116">Bu örnek ayarlar <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> özelliği <xref:System.Windows.Forms.PropertyGrid> için <xref:System.Configuration.UserScopedSettingAttribute> yalnızca kullanıcı ayarı özelliklerini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="f807e-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="f807e-117">Kullanıcı ayarı özellik Kılavuzu eklemek için</span><span class="sxs-lookup"><span data-stu-id="f807e-117">To add a user setting property grid</span></span>  
  
1.  <span data-ttu-id="f807e-118">Ekleme **PropertyGrid** gelen denetim **araç** uygulamanız için tasarım yüzeyine varsayılır burada `Form1`.</span><span class="sxs-lookup"><span data-stu-id="f807e-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="f807e-119">Özellik Kılavuzu denetim varsayılan adı `PropertyGrid1`.</span><span class="sxs-lookup"><span data-stu-id="f807e-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2.  <span data-ttu-id="f807e-120">Tasarım yüzeyi için çift `Form1` form yük olay işleyicisi için kod açın.</span><span class="sxs-lookup"><span data-stu-id="f807e-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3.  <span data-ttu-id="f807e-121">Ayarlama `My.Settings` nesnesi seçili nesne için özellik kılavuzunu olarak.</span><span class="sxs-lookup"><span data-stu-id="f807e-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_1.vb)]  
  
4.  <span data-ttu-id="f807e-122">Yalnızca kullanıcı ayarlarını göstermek için özellik kılavuzunu yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="f807e-122">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_2.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="f807e-123">Yalnızca uygulama kapsamı ayarlarını görüntülemek için kullanın <xref:System.Configuration.ApplicationScopedSettingAttribute> yerine özniteliği <xref:System.Configuration.UserScopedSettingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f807e-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f807e-124">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f807e-124">Robust Programming</span></span>  
 <span data-ttu-id="f807e-125">Uygulama kapatıldığında uygulama kullanıcı ayarlarını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f807e-125">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="f807e-126">Ayarlar hemen kaydetmek için arama `My.Settings.Save` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f807e-126">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="f807e-127">Daha fazla bilgi için bkz: [nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="f807e-127">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f807e-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f807e-128">See Also</span></span>  
 [<span data-ttu-id="f807e-129">My.Settings nesnesi</span><span class="sxs-lookup"><span data-stu-id="f807e-129">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="f807e-130">Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma</span><span class="sxs-lookup"><span data-stu-id="f807e-130">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [<span data-ttu-id="f807e-131">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="f807e-131">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="f807e-132">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını sürdürmek</span><span class="sxs-lookup"><span data-stu-id="f807e-132">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="f807e-133">Uygulama ayarları (.NET) yönetme</span><span class="sxs-lookup"><span data-stu-id="f807e-133">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
