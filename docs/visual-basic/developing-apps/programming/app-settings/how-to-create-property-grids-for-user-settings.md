---
title: "Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzu oluşturma"
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: 5f4b962762aeecea65748c5456bc4a2d75595d4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311623"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="3b2d6-102">Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzu oluşturma</span><span class="sxs-lookup"><span data-stu-id="3b2d6-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>
<span data-ttu-id="3b2d6-103">Kullanıcı ayarları için bir özellik kılavuzunda doldurarak oluşturabileceğiniz bir <xref:System.Windows.Forms.PropertyGrid> kullanıcı ayarı özelliklerini denetimiyle `My.Settings` nesne.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b2d6-104">Çalışmak bu örneğin sırada, uygulamanızın kullanıcı ayarlarına yapılandırılmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="3b2d6-105">Daha fazla bilgi için [uygulama ayarlarını yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="3b2d6-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="3b2d6-106">`My.Settings` Nesnesi, her ayarın bir özellik olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="3b2d6-107">Özellik adı ayar adı ile aynıdır ve özellik türü ayar türü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="3b2d6-108">Ayarın **kapsam** özelliği salt okunur; olup olmadığını belirler özellik için bir **uygulama**-kapsam ayardır sırasında özelliği salt okunur bir **kullanıcı**-kapsam okuma-yazma ayardır.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="3b2d6-109">Daha fazla bilgi için [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="3b2d6-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b2d6-110">Değiştiremez veya çalışma zamanında uygulama kapsamı ayarlarının değerleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="3b2d6-111">Uygulama kapsamı ayarları, yalnızca uygulama oluşturulurken değiştirilebilir (aracılığıyla **Proje Tasarımcısı**) veya uygulama yapılandırma dosyasını düzenleyerek.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="3b2d6-112">Daha fazla bilgi için [uygulama ayarlarını yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="3b2d6-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="3b2d6-113">Bu örnekte bir <xref:System.Windows.Forms.PropertyGrid> kullanıcı ayarı özelliklerine erişmek için Denetim `My.Settings` nesne.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="3b2d6-114">Varsayılan olarak, <xref:System.Windows.Forms.PropertyGrid> tüm özelliklerini gösterir `My.Settings` nesne.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="3b2d6-115">Ancak, kullanıcı ayarı özelliklerine sahip <xref:System.Configuration.UserScopedSettingAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="3b2d6-116">Bu örnekte ayarlar <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> özelliği <xref:System.Windows.Forms.PropertyGrid> için <xref:System.Configuration.UserScopedSettingAttribute> yalnızca kullanıcı ayarı özelliklerini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="3b2d6-117">Bir kullanıcı ayarı özellik kılavuzunda eklemek için</span><span class="sxs-lookup"><span data-stu-id="3b2d6-117">To add a user setting property grid</span></span>  
  
1. <span data-ttu-id="3b2d6-118">Ekleme **PropertyGrid** denetimi **araç kutusu** uygulamanız için tasarım yüzeyine varsayılır burada `Form1`.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="3b2d6-119">Özellik Kılavuzu denetimini varsayılan adıdır `PropertyGrid1`.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2. <span data-ttu-id="3b2d6-120">Tasarım yüzeyi için çift `Form1` form-load olay işleyicisinde kodu açın.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3. <span data-ttu-id="3b2d6-121">Ayarlama `My.Settings` seçili nesne için özellik kılavuzu olarak nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. <span data-ttu-id="3b2d6-122">Özellik Kılavuzu, yalnızca kullanıcı ayarlarını yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-122">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    >  <span data-ttu-id="3b2d6-123">Yalnızca uygulama kapsamlı ayarlar göstermek için kullanın <xref:System.Configuration.ApplicationScopedSettingAttribute> özniteliği yerine <xref:System.Configuration.UserScopedSettingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3b2d6-124">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="3b2d6-124">Robust Programming</span></span>  
 <span data-ttu-id="3b2d6-125">Uygulama kapatıldığında kullanıcı ayarlarını uygulamayı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-125">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="3b2d6-126">Hemen ayarları kaydetmek için çağrı `My.Settings.Save` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-126">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="3b2d6-127">Daha fazla bilgi için [nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="3b2d6-127">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b2d6-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b2d6-128">See also</span></span>

- [<span data-ttu-id="3b2d6-129">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="3b2d6-129">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="3b2d6-130">Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma</span><span class="sxs-lookup"><span data-stu-id="3b2d6-130">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="3b2d6-131">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="3b2d6-131">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="3b2d6-132">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma</span><span class="sxs-lookup"><span data-stu-id="3b2d6-132">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="3b2d6-133">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="3b2d6-133">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
