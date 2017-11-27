---
title: "Özel Denetimler için Uygulama Ayarları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f8292ac459a2943376229ef62466b0a772430dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="application-settings-for-custom-controls"></a><span data-ttu-id="f10cc-102">Özel Denetimler için Uygulama Ayarları</span><span class="sxs-lookup"><span data-stu-id="f10cc-102">Application Settings for Custom Controls</span></span>
<span data-ttu-id="f10cc-103">Özel denetimler denetimleri üçüncü taraf uygulamalarda barındırıldığında uygulama ayarlarını sürdürmek vermek için belirli görevleri tamamlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f10cc-103">You must complete certain tasks to give your custom controls the ability to persist application settings when the controls are hosted in third-party applications.</span></span>  
  
 <span data-ttu-id="f10cc-104">Uygulama ayarları özelliği ilgili belgelere çoğunu bağımsız uygulama oluşturmakta olduğunuz varsayılır altında yazılır.</span><span class="sxs-lookup"><span data-stu-id="f10cc-104">Most of the documentation about the Application Settings feature is written under the assumption that you are creating a standalone application.</span></span> <span data-ttu-id="f10cc-105">Diğer geliştiriciler barındıracak bir denetim uygulamalarında oluşturuyorsanız, ancak denetim ayarlarını kalıcı hale getirmek için bazı ek adımlar uygulamanız ihtiyacınız düzgün.</span><span class="sxs-lookup"><span data-stu-id="f10cc-105">However, if you are creating a control that other developers will host in their applications, you need to take a few additional steps for your control to persist its settings properly.</span></span>  
  
## <a name="application-settings-and-custom-controls"></a><span data-ttu-id="f10cc-106">Uygulama ayarları ve özel denetimler</span><span class="sxs-lookup"><span data-stu-id="f10cc-106">Application Settings and Custom Controls</span></span>  
 <span data-ttu-id="f10cc-107">Denetiminizi düzgün ayarlarını kalıcı hale getirmek, bu işlem türetilen ayarları sarmalayıcı sınıfı, kendi özel uygulamaları oluşturarak sarmalamalıdır <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="f10cc-107">For your control to properly persist its settings, it must encapsulate the process by creating its own dedicated applications settings wrapper class, derived from <xref:System.Configuration.ApplicationSettingsBase>.</span></span> <span data-ttu-id="f10cc-108">Ayrıca, ana denetim sınıfı uygulamalıdır <xref:System.Configuration.IPersistComponentSettings>.</span><span class="sxs-lookup"><span data-stu-id="f10cc-108">Additionally, the main control class must implement the <xref:System.Configuration.IPersistComponentSettings>.</span></span> <span data-ttu-id="f10cc-109">Arabirim iki yöntem yanı sıra çeşitli özellikler içerir <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> ve <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>.</span><span class="sxs-lookup"><span data-stu-id="f10cc-109">The interface contains several properties as well as two methods, <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> and <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>.</span></span> <span data-ttu-id="f10cc-110">Kullanarak bir form denetiminizi eklerseniz **Windows Form Tasarımcısı** Visual Studio'da Windows Forms çağıracak <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> otomatik olarak zaman denetim başlatılır; çağırmalısınız <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> kendiniz `Dispose` Denetim yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f10cc-110">If you add your control to a form using the **Windows Forms Designer** in Visual Studio, Windows Forms will call <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automatically when the control is initialized; you must call <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> yourself in the `Dispose` method of your control.</span></span>  
  
 <span data-ttu-id="f10cc-111">Ayrıca, Visual Studio tasarım-zamanı ortamlarda düzgün çalışması özel denetimler için uygulama ayarları için sırayla aşağıdakileri uygulamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="f10cc-111">In addition, you should implement the following in order for application settings for custom controls to work properly in design-time environments such as Visual Studio:</span></span>  
  
1.  <span data-ttu-id="f10cc-112">Özel uygulama ayarlarını sınıf alan Oluşturucu ile bir <xref:System.ComponentModel.IComponent> tek bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="f10cc-112">A custom application settings class with a constructor that takes an <xref:System.ComponentModel.IComponent> as a single parameter.</span></span> <span data-ttu-id="f10cc-113">Bu sınıf, kaydetme ve uygulama ayarlarının tümünü yükleme kullanın.</span><span class="sxs-lookup"><span data-stu-id="f10cc-113">Use this class to save and load all of your application settings.</span></span> <span data-ttu-id="f10cc-114">Bu sınıfın yeni bir örneğini oluştururken Oluşturucusu kullanarak özel denetim geçirin.</span><span class="sxs-lookup"><span data-stu-id="f10cc-114">When you create a new instance of this class, pass your custom control using the constructor.</span></span>  
  
2.  <span data-ttu-id="f10cc-115">Denetim oluşturulur ve bir form üzerinde gibi formun yerleştirilen sonra bu özel ayarları sınıfı oluşturmak <xref:System.Windows.Forms.Form.Load> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="f10cc-115">Create this custom settings class after the control has been created and placed on a form, such as in the form's <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
 <span data-ttu-id="f10cc-116">Özel ayarlar sınıfı oluşturma ile ilgili yönergeler için bkz: [nasıl yapılır: uygulama ayarları oluştur](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span><span class="sxs-lookup"><span data-stu-id="f10cc-116">For instructions on creating a custom settings class, see [How to: Create Application Settings](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span></span>  
  
## <a name="settings-keys-and-shared-settings"></a><span data-ttu-id="f10cc-117">Ayarları anahtarları ve paylaşılan ayarları</span><span class="sxs-lookup"><span data-stu-id="f10cc-117">Settings Keys and Shared Settings</span></span>  
 <span data-ttu-id="f10cc-118">Bazı denetimler aynı form içindeki birden çok kez kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f10cc-118">Some controls can be used multiple times within the same form.</span></span> <span data-ttu-id="f10cc-119">Çoğu zaman, tek tek kendi ayarlarını sürdürmek için bu denetimleri isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f10cc-119">Most of the time, you will want these controls to persist their own individual settings.</span></span> <span data-ttu-id="f10cc-120">İle <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> özelliği <xref:System.Configuration.IPersistComponentSettings>, formdaki bir denetime birden fazla sürümünü belirsizliğini ortadan kaldırmak için davranır benzersiz bir dize sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f10cc-120">With the <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> property on <xref:System.Configuration.IPersistComponentSettings>, you can supply a unique string that acts to disambiguate multiple versions of a control on a form.</span></span>  
  
 <span data-ttu-id="f10cc-121">Uygulamak için en basit yolu <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> kullanmaktır <xref:System.Windows.Forms.Control.Name%2A> özelliği için bir denetim <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="f10cc-121">The simplest way to implement <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> is to use the <xref:System.Windows.Forms.Control.Name%2A> property of the control for the <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>.</span></span> <span data-ttu-id="f10cc-122">Yük ya da denetim ayarlarını Kaydet değerini geçirin <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> oturum <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> özelliği <xref:System.Configuration.ApplicationSettingsBase> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f10cc-122">When you load or save the control's settings, you pass the value of <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> on to the <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> property of the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span> <span data-ttu-id="f10cc-123">Uygulama ayarları, kullanıcının ayarlarını XML ediyorsa bu benzersiz anahtar kullanır.</span><span class="sxs-lookup"><span data-stu-id="f10cc-123">Application Settings uses this unique key when it persists the user's settings to XML.</span></span> <span data-ttu-id="f10cc-124">Aşağıdaki örnekte gösterildiği nasıl kod bir `<userSettings>` bölümüne adlı özel bir denetim örneği için bakın `CustomControl1` için bir ayar kaydeder, `Text` özelliği.</span><span class="sxs-lookup"><span data-stu-id="f10cc-124">The following code example shows how a `<userSettings>` section may look for an instance of a custom control named `CustomControl1` that saves a setting for its `Text` property.</span></span>  
  
```xml  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 <span data-ttu-id="f10cc-125">Tüm örnekleri için bir değer sağlamazsanız bir denetimin <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> aynı ayarları paylaşır.</span><span class="sxs-lookup"><span data-stu-id="f10cc-125">Any instances of a control that do not supply a value for <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> will share the same settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f10cc-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f10cc-126">See Also</span></span>  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.IPersistComponentSettings>  
 [<span data-ttu-id="f10cc-127">Uygulama ayarları mimarisi</span><span class="sxs-lookup"><span data-stu-id="f10cc-127">Application Settings Architecture</span></span>](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)
