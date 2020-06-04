---
title: 'Nasıl yapılır: Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: e93c62ad138be260422319e28a3ed85dd1871a1b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410172"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="792ef-102">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="792ef-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>

<span data-ttu-id="792ef-103"><xref:System.Windows.Forms.PropertyGrid>Nesnenin Kullanıcı ayarı özellikleriyle bir denetim doldurarak Kullanıcı ayarları için özellik Kılavuzu oluşturabilirsiniz `My.Settings` .</span><span class="sxs-lookup"><span data-stu-id="792ef-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="792ef-104">Bu örneğin çalışması için, uygulamanız kullanıcı ayarlarının yapılandırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="792ef-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="792ef-105">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="792ef-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="792ef-106">`My.Settings`Nesnesi her ayarı bir özellik olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="792ef-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="792ef-107">Özellik adı, ayar adıyla aynıdır ve özellik türü ayar türüyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="792ef-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="792ef-108">Ayarın **kapsamı** , özelliğin salt okunurdur belirler; bir **uygulama**kapsamı ayarının özelliği salt okunurdur, ancak **Kullanıcı**kapsamı ayarının özelliği okuma-yazma olur.</span><span class="sxs-lookup"><span data-stu-id="792ef-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="792ef-109">Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="792ef-109">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="792ef-110">Çalışma zamanında uygulama kapsamı ayarlarının değerlerini değiştiremez veya kaydedemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="792ef-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="792ef-111">Uygulama kapsamı ayarları yalnızca uygulama oluşturulurken ( **Proje Tasarımcısı**aracılığıyla) veya uygulamanın yapılandırma dosyası düzenlenerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="792ef-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="792ef-112">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="792ef-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="792ef-113">Bu örnek, <xref:System.Windows.Forms.PropertyGrid> nesnenin Kullanıcı ayarı özelliklerine erişmek için bir denetim kullanır `My.Settings` .</span><span class="sxs-lookup"><span data-stu-id="792ef-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="792ef-114">Varsayılan olarak, <xref:System.Windows.Forms.PropertyGrid> nesnesinin tüm özelliklerini gösterir `My.Settings` .</span><span class="sxs-lookup"><span data-stu-id="792ef-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="792ef-115">Ancak, Kullanıcı ayarı özelliklerinin <xref:System.Configuration.UserScopedSettingAttribute> özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="792ef-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="792ef-116">Bu örnek <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> , öğesinin özelliğini <xref:System.Windows.Forms.PropertyGrid> <xref:System.Configuration.UserScopedSettingAttribute> yalnızca Kullanıcı ayarı özelliklerini görüntüleyecek şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="792ef-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="792ef-117">Kullanıcı ayarı Özellik Kılavuzu eklemek için</span><span class="sxs-lookup"><span data-stu-id="792ef-117">To add a user setting property grid</span></span>  
  
1. <span data-ttu-id="792ef-118">**Araç kutusundan** **PropertyGrid** denetimini uygulamanızın tasarım yüzeyine ekleyin, burada kabul edilir `Form1` .</span><span class="sxs-lookup"><span data-stu-id="792ef-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="792ef-119">Özellik Kılavuzu denetiminin varsayılan adı `PropertyGrid1` .</span><span class="sxs-lookup"><span data-stu-id="792ef-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2. <span data-ttu-id="792ef-120">`Form1`Form yükleme olay işleyicisi için kodu açmak üzere tasarım yüzeyine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="792ef-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3. <span data-ttu-id="792ef-121">Nesne, `My.Settings` Özellik kılavuzu için seçilen nesne olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="792ef-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. <span data-ttu-id="792ef-122">Özellik kılavuzunu yalnızca Kullanıcı ayarlarını gösterecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="792ef-122">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > <span data-ttu-id="792ef-123">Yalnızca uygulama kapsamı ayarlarını göstermek için <xref:System.Configuration.ApplicationScopedSettingAttribute> yerine özniteliğini kullanın <xref:System.Configuration.UserScopedSettingAttribute> .</span><span class="sxs-lookup"><span data-stu-id="792ef-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="792ef-124">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="792ef-124">Robust Programming</span></span>  

 <span data-ttu-id="792ef-125">Uygulama kapandığında uygulama kullanıcı ayarlarını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="792ef-125">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="792ef-126">Ayarları hemen kaydetmek için `My.Settings.Save` yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="792ef-126">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="792ef-127">Daha fazla bilgi için bkz. [nasıl yapılır: Kullanıcı ayarlarını Visual Basic kalıcı hale](how-to-persist-user-settings.md)getirme.</span><span class="sxs-lookup"><span data-stu-id="792ef-127">For more information, see [How to: Persist User Settings in Visual Basic](how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="792ef-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="792ef-128">See also</span></span>

- [<span data-ttu-id="792ef-129">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="792ef-129">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="792ef-130">Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma</span><span class="sxs-lookup"><span data-stu-id="792ef-130">How to: Read Application Settings in Visual Basic</span></span>](how-to-read-application-settings.md)
- [<span data-ttu-id="792ef-131">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="792ef-131">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="792ef-132">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma</span><span class="sxs-lookup"><span data-stu-id="792ef-132">How to: Persist User Settings in Visual Basic</span></span>](how-to-persist-user-settings.md)
- [<span data-ttu-id="792ef-133">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="792ef-133">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
