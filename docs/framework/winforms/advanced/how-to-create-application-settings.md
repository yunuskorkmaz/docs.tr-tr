---
title: 'Nasıl yapılır: Uygulama Ayarları Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
ms.openlocfilehash: 5cf109aec8b55650f43f07f5b303c6373df4efc7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305981"
---
# <a name="how-to-create-application-settings"></a><span data-ttu-id="1091d-102">Nasıl yapılır: Uygulama Ayarları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1091d-102">How to: Create Application Settings</span></span>
<span data-ttu-id="1091d-103">Yönetilen kod kullanarak, yeni uygulama ayarları oluşturma ve böylece bu ayarlar yüklenir ve çalışma zamanında otomatik olarak kaydedilir bunları özelliklerine formunuza veya form denetimlerinde bağlayın.</span><span class="sxs-lookup"><span data-stu-id="1091d-103">Using managed code, you can create new application settings and bind them to properties on your form or your form's controls, so that these settings are loaded and saved automatically at run time.</span></span>  
  
 <span data-ttu-id="1091d-104">Aşağıdaki yordamda, el ile türetilen bir sarmalayıcı sınıfı oluşturmanız <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="1091d-104">In the following procedure, you manually create a wrapper class that derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span> <span data-ttu-id="1091d-105">Bu sınıf için kullanıma sunmak istediğiniz her uygulama ayarı için ortak olarak erişilebilen bir özellik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1091d-105">To this class you add a publicly accessible property for each application setting that you want to expose.</span></span>  
  
 <span data-ttu-id="1091d-106">Ayrıca, bu yordamı Visual Studio Tasarımcısı'nda çok az kod kullanarak gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1091d-106">You can also perform this procedure using minimal code in the Visual Studio designer.</span></span>  <span data-ttu-id="1091d-107">Ayrıca bkz: [nasıl yapılır: Tasarımcıyı kullanarak uygulama ayarları oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1091d-107">Also see [How to: Create Application Settings Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100)).</span></span>  
  
### <a name="to-create-new-application-settings-programmatically"></a><span data-ttu-id="1091d-108">Yeni uygulama ayarları program aracılığıyla oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1091d-108">To create new Application Settings programmatically</span></span>  
  
1. <span data-ttu-id="1091d-109">Projenize yeni bir sınıf ekleyin ve adlandırın.</span><span class="sxs-lookup"><span data-stu-id="1091d-109">Add a new class to your project, and rename it.</span></span> <span data-ttu-id="1091d-110">Bu yordam için Biz bu sınıf göndereceği `MyUserSettings`.</span><span class="sxs-lookup"><span data-stu-id="1091d-110">For this procedure, we will call this class `MyUserSettings`.</span></span> <span data-ttu-id="1091d-111">Sınıf tanımını değiştirin, böylece bu sınıfın türetildiği <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="1091d-111">Change the class definition so that the class derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span>  
  
2. <span data-ttu-id="1091d-112">Bu sarmalayıcı sınıf için ihtiyaç duyduğunuz her uygulama ayarı üzerinde bir özellik tanımlayın ve bu özellik ile ya da geçerli <xref:System.Configuration.ApplicationScopedSettingAttribute> veya <xref:System.Configuration.UserScopedSettingAttribute>ayarı kapsamını bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="1091d-112">Define a property on this wrapper class for each application setting you require, and apply that property with either the <xref:System.Configuration.ApplicationScopedSettingAttribute> or <xref:System.Configuration.UserScopedSettingAttribute>, depending on the scope of the setting.</span></span> <span data-ttu-id="1091d-113">Ayar kapsamı hakkında daha fazla bilgi için bkz: [uygulama ayarlarına genel bakış](application-settings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1091d-113">For more information about settings scope, see [Application Settings Overview](application-settings-overview.md).</span></span> <span data-ttu-id="1091d-114">Artık, kodunuz şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="1091d-114">By now, your code should look like this:</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3. <span data-ttu-id="1091d-115">Uygulamanızda bu sarmalayıcı sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1091d-115">Create an instance of this wrapper class in your application.</span></span> <span data-ttu-id="1091d-116">Bu genellikle ana formu özel üyesi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1091d-116">It will commonly be a private member of the main form.</span></span> <span data-ttu-id="1091d-117">Sınıfınıza tanımladığınıza göre bir özelliğine bağlamak gerekir; Bu durumda, <xref:System.Windows.Forms.Form.BackColor%2A> formunuza bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="1091d-117">Now that you have defined your class, you need to bind it to a property; in this case, the <xref:System.Windows.Forms.Form.BackColor%2A> property of your form.</span></span> <span data-ttu-id="1091d-118">Bunu, formun içinde gerçekleştirebilirsiniz `Load` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="1091d-118">You can accomplish this in your form's `Load` event handler.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="1091d-119">Çalışma zamanında ayarlarını değiştirmek için bir yol sağlar, kullanıcının geçerli ayarlarının formunuza kapatır, aksi takdirde, bu değişiklikler kaybolacak diske kaydetmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="1091d-119">If you provide a way to change settings at run time, you will need to save the user's current settings to disk when your form closes, or else these changes will be lost.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#3](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     <span data-ttu-id="1091d-120">Artık başarıyla oluşturulmuş yeni bir uygulama ayarı ve belirtilen özelliğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1091d-120">You have now successfully created a new application setting and bound it to the specified property.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1091d-121">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="1091d-121">.NET Framework Security</span></span>  
 <span data-ttu-id="1091d-122">Varsayılan ayar sağlayıcısı <xref:System.Configuration.LocalFileSettingsProvider>, yapılandırma dosyalarındaki bilgileri düz metin olarak kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="1091d-122">The default settings provider, <xref:System.Configuration.LocalFileSettingsProvider>, persists information to configuration files as plain text.</span></span> <span data-ttu-id="1091d-123">Bu, geçerli kullanıcı için işletim sistemi tarafından sağlanan dosya erişim güvenliği için güvenlik sınırlar.</span><span class="sxs-lookup"><span data-stu-id="1091d-123">This limits security to the file access security provided by the operating system for the current user.</span></span> <span data-ttu-id="1091d-124">Bu nedenle dikkatli yapılandırma dosyalarında depolanan bilgileri alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1091d-124">Because of this, care must be taken with the information stored in configuration files.</span></span> <span data-ttu-id="1091d-125">Örneğin, bir uygulama ayarları uygulamanın veri deposuna işaret eden bağlantı dizeleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1091d-125">For example, one common use for application settings is to store connection strings that point to the application's data store.</span></span> <span data-ttu-id="1091d-126">Ancak, güvenlik kaygıları nedeniyle, parolalar gibi dizeleri içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="1091d-126">However, because of security concerns, such strings should not include passwords.</span></span> <span data-ttu-id="1091d-127">Bağlantı dizeleri hakkında daha fazla bilgi için bkz. <xref:System.Configuration.SpecialSetting>.</span><span class="sxs-lookup"><span data-stu-id="1091d-127">For more information about connection strings, see <xref:System.Configuration.SpecialSetting>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1091d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1091d-128">See also</span></span>

- <xref:System.Configuration.SpecialSettingAttribute>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [<span data-ttu-id="1091d-129">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1091d-129">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="1091d-130">Nasıl yapılır: Uygulama ayarlarını doğrulama</span><span class="sxs-lookup"><span data-stu-id="1091d-130">How to: Validate Application Settings</span></span>](how-to-validate-application-settings.md)
