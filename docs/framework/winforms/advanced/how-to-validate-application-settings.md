---
title: 'Nasıl yapılır: Uygulama Ayarlarını Doğrulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating application settings
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], validating
ms.assetid: 9f145ada-4267-436a-aa4c-c4dcffd0afb7
ms.openlocfilehash: aa8877150d654bf9659dbb34b91436c0ee9ff8b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526301"
---
# <a name="how-to-validate-application-settings"></a><span data-ttu-id="9e911-102">Nasıl yapılır: Uygulama Ayarlarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="9e911-102">How to: Validate Application Settings</span></span>
<span data-ttu-id="9e911-103">Bu konu, kalıcı yapılan önce uygulama ayarlarını doğrulama gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9e911-103">This topic demonstrates how to validate application settings before they are persisted.</span></span>  
  
 <span data-ttu-id="9e911-104">Uygulama ayarları kesin türü belirtilmiş olduğundan, kullanıcılar için belirli bir ayarı yanlış türde veri atayamazsınız bazı size güven verir.</span><span class="sxs-lookup"><span data-stu-id="9e911-104">Because application settings are strongly typed, you have some confidence that users cannot assign data of an incorrect type to a given setting.</span></span> <span data-ttu-id="9e911-105">Ancak, kullanıcı hala kabul edilebilir sınırların dışında kalan bir ayar için bir değer atamaya deneyebilir — Örneğin, gelecekte oluşan bir doğum tarihi sağlama.</span><span class="sxs-lookup"><span data-stu-id="9e911-105">However, a user still may attempt to assign a value to a setting that falls outside of acceptable bounds—for example, supplying a birth date that occurs in the future.</span></span> <span data-ttu-id="9e911-106"><xref:System.Configuration.ApplicationSettingsBase>, tüm uygulama ayarlarını sınıfları, üst sınıfının denetimi gibi sınırları etkinleştirmek için dört olayları gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e911-106"><xref:System.Configuration.ApplicationSettingsBase>, the parent class of all application settings classes, exposes four events to enable such bounds checking.</span></span> <span data-ttu-id="9e911-107">Bu olayları işleme tüm doğrulama kodunuzu boyunca projenizin Saçılma yerine tek bir konuma yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="9e911-107">Handling these events puts all of your validation code in a single location, rather than scattering it throughout your project.</span></span>  
  
 <span data-ttu-id="9e911-108">Aşağıdaki tabloda açıklandığı gibi ayarlarınızı doğrulamanıza gerektiğinde, kullandığınız olay bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9e911-108">The event you use depends upon when you need to validate your settings, as described in the following table.</span></span>  
  
|<span data-ttu-id="9e911-109">Olay</span><span class="sxs-lookup"><span data-stu-id="9e911-109">Event</span></span>|<span data-ttu-id="9e911-110">Geçişi ve kullanımı</span><span class="sxs-lookup"><span data-stu-id="9e911-110">Occurrence and use</span></span>|  
|-----------|------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|<span data-ttu-id="9e911-111">Ayarlar özellik grubu ilk yüklemeden sonra oluşur.</span><span class="sxs-lookup"><span data-stu-id="9e911-111">Occurs after the initial loading of a settings property group.</span></span><br /><br /> <span data-ttu-id="9e911-112">Bu olay, uygulama içinde kullanılmadan önce tüm özellik grubu için başlangıç değerlerini doğrulamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e911-112">Use this event to validate initial values for the entire property group before they are used within the application.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|<span data-ttu-id="9e911-113">Bir tek ayarları özelliğinin değeri değiştirilmeden önce gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="9e911-113">Occurs before the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="9e911-114">Bu olay, değiştirilmeden önce tek bir özellik doğrulamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e911-114">Use this event to validate a single property before it is changed.</span></span> <span data-ttu-id="9e911-115">Kullanıcılar kendi eylemleri ve seçenekler ile ilgili anında geri bildirim sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e911-115">It can provide immediate feedback to users regarding their actions and choices.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|<span data-ttu-id="9e911-116">Bir tek ayarları özelliğinin değeri değiştikten sonra gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="9e911-116">Occurs after the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="9e911-117">Bu olay, değiştirildikten sonra tek bir özellik doğrulamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e911-117">Use this event to validate a single property after it is changed.</span></span> <span data-ttu-id="9e911-118">Uzun ve zaman uyumsuz doğrulama işlemi gerekli olmadığı sürece bu olay için doğrulama nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e911-118">This event is rarely used for validation unless a lengthy, asynchronous validation process is required.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|<span data-ttu-id="9e911-119">Ayarlar özellik grubunda depolanan önce gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="9e911-119">Occurs before the settings property group is stored.</span></span><br /><br /> <span data-ttu-id="9e911-120">Kalıcı yapılan önce tüm özellik grubunun değerlerini doğrulamak için bu olayı kullanın diske.</span><span class="sxs-lookup"><span data-stu-id="9e911-120">Use this event to validate values for the entire property group before they are persisted to disk.</span></span>|  
  
 <span data-ttu-id="9e911-121">Tipik olarak, tüm bu olayları aynı uygulamadaki doğrulama amacıyla kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="9e911-121">Typically, you will not use all of these events within the same application for validation purposes.</span></span> <span data-ttu-id="9e911-122">Örneğin, genellikle yalnızca işleyerek tüm doğrulama gereksinimlerini karşılamak mümkündür <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> olay.</span><span class="sxs-lookup"><span data-stu-id="9e911-122">For example, it is often possible to fulfill all validation requirements by handling only the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>  
  
 <span data-ttu-id="9e911-123">Geçersiz bir değer algıladığında, olay işleyici genellikle aşağıdaki eylemlerden birini gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="9e911-123">An event handler generally performs one of the following actions when it detects an invalid value:</span></span>  
  
-   <span data-ttu-id="9e911-124">Otomatik olarak gibi varsayılan değeri doğru olması için bilinen bir değerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e911-124">Automatically supplies a value known to be correct, such as the default value.</span></span>  
  
-   <span data-ttu-id="9e911-125">Bilgi için sunucu kodu kullanıcı yeniden sorgular.</span><span class="sxs-lookup"><span data-stu-id="9e911-125">Re-queries the user of server code for information.</span></span>  
  
-   <span data-ttu-id="9e911-126">İlişkili eylemlerinin önce aşağıdaki gibi başlatılan olayları için <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> ve <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, kullanan <xref:System.ComponentModel.CancelEventArgs> işlemi iptal etmek için bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="9e911-126">For events raised before their associated actions, such as <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> and <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, uses the <xref:System.ComponentModel.CancelEventArgs> argument to cancel the operation.</span></span>  
  
 <span data-ttu-id="9e911-127">Olay işleme hakkında daha fazla bilgi için bkz: [olay işleyicilerine genel bakış](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9e911-127">For more information about event handling, see [Event Handlers Overview](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="9e911-128">Aşağıdaki yordamları kullanarak geçerli doğum tarihini test etme Göster <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> veya <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> olay.</span><span class="sxs-lookup"><span data-stu-id="9e911-128">The following procedures show how to test for a valid birth date using either the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> or the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span> <span data-ttu-id="9e911-129">Yordamlar, uygulamanızın ayarlarını önceden oluşturduğunuz varsayım altında yazılmış; Bu örnekte, adlı bir ayarda denetimi sınırları gerçekleştiririz `DateOfBirth`.</span><span class="sxs-lookup"><span data-stu-id="9e911-129">The procedures were written under the assumption that you have already created your application settings; in this example, we will perform bounds checking on a setting named `DateOfBirth`.</span></span> <span data-ttu-id="9e911-130">Ayarları oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: uygulama ayarları oluştur](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span><span class="sxs-lookup"><span data-stu-id="9e911-130">For more information about creating settings, see [How to: Create Application Settings](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span></span>  
  
### <a name="to-obtain-the-application-settings-object"></a><span data-ttu-id="9e911-131">Uygulama Ayarları nesnesini almak için</span><span class="sxs-lookup"><span data-stu-id="9e911-131">To obtain the application settings object</span></span>  
  
-   <span data-ttu-id="9e911-132">Uygulama Ayarları nesnesini (sarmalayıcı örneği) referansı aşağıdaki madde işaretli öğelerden birini tamamlayarak alın:</span><span class="sxs-lookup"><span data-stu-id="9e911-132">Obtain a reference to the application settings object (the wrapper instance) by completing one of the following bulleted items:</span></span>  
  
    -   <span data-ttu-id="9e911-133">Visual Studio uygulama ayarları iletişim kutusunda kullanarak ayarlarınızı oluşturduysanız **Özellik Düzenleyici**, dilinizi ifadesini aracılığıyla oluşturulan varsayılan ayarları nesnesi alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e911-133">If you created your settings using the Visual Studio Application Settings dialog box in the **Property Editor**, you can retrieve the default settings object generated for your language through the following expression.</span></span>  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         <span data-ttu-id="9e911-134">-veya-</span><span class="sxs-lookup"><span data-stu-id="9e911-134">-or-</span></span>  
  
    -   <span data-ttu-id="9e911-135">Visual Basic Geliştirici misiniz ve uygulama ayarlarınızı, Proje Tasarımcısı'nı kullanarak oluşturduğunuz, kullanarak ayarlarınızı alabilirsiniz [My.Settings nesnesi](~/docs/visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="9e911-135">If you are a Visual Basic developer and you created your application settings using the Project Designer, you can retrieve your settings by using the [My.Settings Object](~/docs/visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
         <span data-ttu-id="9e911-136">-veya-</span><span class="sxs-lookup"><span data-stu-id="9e911-136">-or-</span></span>  
  
    -   <span data-ttu-id="9e911-137">Türetme tarafından ayarlarınızı oluşturduysanız <xref:System.Configuration.ApplicationSettingsBase> doğrudan sınıfınız el ile örneği gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e911-137">If you created your settings by deriving from <xref:System.Configuration.ApplicationSettingsBase> directly, you need to instantiate your class manually.</span></span>  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 <span data-ttu-id="9e911-138">Aşağıdaki yordamlar, uygulama ayarları nesnesi bu yordam son madde işaretli öğenin tamamlayarak edinilen varsayımına altında yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="9e911-138">The following procedures were written under the assumption that the application settings object was obtained by completing the last bulleted item in this procedure.</span></span>  
  
### <a name="to-validate-application-settings-when-a-setting-is-changing"></a><span data-ttu-id="9e911-139">Bir ayarı değiştirirken uygulama ayarlarını doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="9e911-139">To validate Application Settings when a setting is changing</span></span>  
  
1.  <span data-ttu-id="9e911-140">C# Geliştirici, form veya denetimin olup olmadığını `Load` olayı için bir olay işleyicisi ekleme <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> olay.</span><span class="sxs-lookup"><span data-stu-id="9e911-140">If you are a C# developer, in your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>  
  
     <span data-ttu-id="9e911-141">-veya-</span><span class="sxs-lookup"><span data-stu-id="9e911-141">-or-</span></span>  
  
     <span data-ttu-id="9e911-142">Visual Basic Geliştirici olup, bildirmelidir `Settings` değişken kullanarak `WithEvents` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="9e911-142">If you are a Visual Basic developer, you should declare the `Settings` variable using the `WithEvents` keyword.</span></span>  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        settings.SettingChanging += new SettingChangingEventHandler(MyCustomSettings_SettingChanging);  
    }  
    ```  
  
    ```vb  
    Public Sub Form1_Load(sender as Object, e as EventArgs)  
        AddHandler settings.SettingChanging, AddressOf MyCustomSettings_SettingChanging  
    End Sub   
    ```  
  
2.  <span data-ttu-id="9e911-143">Olay işleyicisi tanımlama ve içinde sınırları doğum tarihi denetimi gerçekleştirmek için kod yazma.</span><span class="sxs-lookup"><span data-stu-id="9e911-143">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>  
  
    ```csharp  
    private void MyCustomSettings_SettingChanging(Object sender, SettingChangingEventArgs e)  
    {  
        if (e.SettingName.Equals("DateOfBirth")) {  
            Date newDate = (Date)e.NewValue;  
            If (newDate > Date.Now) {  
                e.Cancel = true;  
                // Inform the user.  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub MyCustomSettings_SettingChanging(sender as Object, e as SettingChangingEventArgs) Handles Settings.SettingChanging  
        If (e.SettingName.Equals("DateOfBirth")) Then  
            Dim NewDate as Date = CType(e.NewValue, Date)  
            If (NewDate > Date.Now) Then  
                e.Cancel = True  
                ' Inform the user.  
            End If  
        End If  
    End Sub  
    ```  
  
### <a name="to-validate-application-settings-when-a-save-occurs"></a><span data-ttu-id="9e911-144">Uygulama ayarları kaydetme zaman doğrulamak için oluşur</span><span class="sxs-lookup"><span data-stu-id="9e911-144">To validate Application Settings when a Save occurs</span></span>  
  
1.  <span data-ttu-id="9e911-145">Form veya denetimin `Load` olayı için bir olay işleyicisi ekleme <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> olay.</span><span class="sxs-lookup"><span data-stu-id="9e911-145">In your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span>  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        settings.SettingsSaving += new SettingsSavingEventHandler(MyCustomSettings_SettingsSaving);  
    }  
    ```  
  
    ```vb  
    Public Sub Form1_Load(Sender as Object, e as EventArgs)  
        AddHandler settings.SettingsSaving, AddressOf MyCustomSettings_SettingsSaving  
    End Sub  
    ```  
  
2.  <span data-ttu-id="9e911-146">Olay işleyicisi tanımlama ve içinde sınırları doğum tarihi denetimi gerçekleştirmek için kod yazma.</span><span class="sxs-lookup"><span data-stu-id="9e911-146">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>  
  
    ```csharp  
    private void MyCustomSettings_SettingsSaving(Object sender, SettingsSavingEventArgs e)  
    {  
        if (this["DateOfBirth"] > Date.Now) {  
            e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub MyCustomSettings_SettingsSaving(Sender as Object, e as SettingsSavingEventArgs)  
        If (Me["DateOfBirth"] > Date.Now) Then  
            e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9e911-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e911-147">See Also</span></span>  
 [<span data-ttu-id="9e911-148">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9e911-148">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="9e911-149">Nasıl yapılır: Uygulama Ayarları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9e911-149">How to: Create Application Settings</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)
