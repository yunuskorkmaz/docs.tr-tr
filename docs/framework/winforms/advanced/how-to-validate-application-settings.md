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
ms.openlocfilehash: 220b86c0de57e60036527bb49f2d8de46390a9ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929786"
---
# <a name="how-to-validate-application-settings"></a><span data-ttu-id="7b3f1-102">Nasıl yapılır: Uygulama Ayarlarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="7b3f1-102">How to: Validate Application Settings</span></span>

<span data-ttu-id="7b3f1-103">Bu konuda, uygulama ayarlarının kalıcı olmadan önce nasıl doğrulanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-103">This topic demonstrates how to validate application settings before they are persisted.</span></span>

<span data-ttu-id="7b3f1-104">Uygulama ayarları kesin olarak yazıldığından, kullanıcıların yanlış türde verileri belirli bir ayara atayamadığı bazı güvenlerdir.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-104">Because application settings are strongly typed, you have some confidence that users cannot assign data of an incorrect type to a given setting.</span></span> <span data-ttu-id="7b3f1-105">Bununla birlikte, bir Kullanıcı, kabul edilebilir sınırların dışında kalan bir ayara bir değer atamayı deneyebilir (örneğin, gelecekte oluşan bir Doğum tarihi sağlama).</span><span class="sxs-lookup"><span data-stu-id="7b3f1-105">However, a user still may attempt to assign a value to a setting that falls outside of acceptable bounds—for example, supplying a birth date that occurs in the future.</span></span> <span data-ttu-id="7b3f1-106"><xref:System.Configuration.ApplicationSettingsBase>Tüm uygulama ayarları sınıflarının üst sınıfı, bu tür sınırlar denetimini etkinleştirmek için dört olay sunar.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-106"><xref:System.Configuration.ApplicationSettingsBase>, the parent class of all application settings classes, exposes four events to enable such bounds checking.</span></span> <span data-ttu-id="7b3f1-107">Bu olayları işlemek, tüm doğrulama kodunuzu projeniz genelinde saçmak yerine tek bir konuma koyar.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-107">Handling these events puts all of your validation code in a single location, rather than scattering it throughout your project.</span></span>

<span data-ttu-id="7b3f1-108">Kullandığınız olay, aşağıdaki tabloda açıklandığı gibi ayarlarınızı doğrulamanız gerektiğinde değişir.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-108">The event you use depends upon when you need to validate your settings, as described in the following table.</span></span>

|<span data-ttu-id="7b3f1-109">Olay</span><span class="sxs-lookup"><span data-stu-id="7b3f1-109">Event</span></span>|<span data-ttu-id="7b3f1-110">Oluşum ve kullanım</span><span class="sxs-lookup"><span data-stu-id="7b3f1-110">Occurrence and use</span></span>|
|-----------|------------------------|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|<span data-ttu-id="7b3f1-111">Bir ayarlar özellik grubunun ilk yüklemesiyle sonra oluşur.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-111">Occurs after the initial loading of a settings property group.</span></span><br /><br /> <span data-ttu-id="7b3f1-112">Uygulama içinde kullanılmadan önce tüm özellik grubunun başlangıç değerlerini doğrulamak için bu olayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-112">Use this event to validate initial values for the entire property group before they are used within the application.</span></span>|
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|<span data-ttu-id="7b3f1-113">Tek bir Settings özelliğinin değeri değiştirilmeden önce oluşur.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-113">Occurs before the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="7b3f1-114">Değiştirilmeden önce tek bir özelliği doğrulamak için bu olayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-114">Use this event to validate a single property before it is changed.</span></span> <span data-ttu-id="7b3f1-115">Bu, kullanıcılara eylemlerle ve seçimleriyle ilgili anında geri bildirim sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-115">It can provide immediate feedback to users regarding their actions and choices.</span></span>|
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|<span data-ttu-id="7b3f1-116">Tek bir Settings özelliğinin değeri değiştirildikten sonra gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-116">Occurs after the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="7b3f1-117">Değiştirildikten sonra tek bir özelliği doğrulamak için bu olayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-117">Use this event to validate a single property after it is changed.</span></span> <span data-ttu-id="7b3f1-118">Bu olay, daha uzun bir zaman uyumsuz doğrulama işlemi gerekli olmadığı sürece doğrulama için nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-118">This event is rarely used for validation unless a lengthy, asynchronous validation process is required.</span></span>|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|<span data-ttu-id="7b3f1-119">Ayarlar özellik grubu depolanmadan önce oluşur.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-119">Occurs before the settings property group is stored.</span></span><br /><br /> <span data-ttu-id="7b3f1-120">Tüm özellik grubu değerlerini diske kalıcı yapmadan önce doğrulamak için bu olayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-120">Use this event to validate values for the entire property group before they are persisted to disk.</span></span>|

<span data-ttu-id="7b3f1-121">Genellikle, doğrulama amacıyla aynı uygulama içinde bu olayların tümünü kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-121">Typically, you will not use all of these events within the same application for validation purposes.</span></span> <span data-ttu-id="7b3f1-122">Örneğin, genellikle yalnızca <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> olayını işleyerek tüm doğrulama gereksinimlerinin yerine getirilmesi mümkündür.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-122">For example, it is often possible to fulfill all validation requirements by handling only the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>

<span data-ttu-id="7b3f1-123">Bir olay işleyicisi, geçersiz bir değer algıladığında, genellikle aşağıdaki eylemlerden birini gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="7b3f1-123">An event handler generally performs one of the following actions when it detects an invalid value:</span></span>

- <span data-ttu-id="7b3f1-124">, Varsayılan değer gibi, doğru olarak bilinen bir değeri otomatik olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-124">Automatically supplies a value known to be correct, such as the default value.</span></span>

- <span data-ttu-id="7b3f1-125">Bilgi için sunucu kodu kullanıcısını yeniden sorgular.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-125">Re-queries the user of server code for information.</span></span>

- <span data-ttu-id="7b3f1-126"><xref:System.Configuration.ApplicationSettingsBase.SettingChanging> <xref:System.ComponentModel.CancelEventArgs> Ve gibiilişkilieylemlerindenönceoluşturulanolaylariçin,işlemiiptaletmekiçinbağımsızdeğişkeninikullanır.<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving></span><span class="sxs-lookup"><span data-stu-id="7b3f1-126">For events raised before their associated actions, such as <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> and <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, uses the <xref:System.ComponentModel.CancelEventArgs> argument to cancel the operation.</span></span>

<span data-ttu-id="7b3f1-127">Olay işleme hakkında daha fazla bilgi için bkz. [olay Işleyicilerine genel bakış](../event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7b3f1-127">For more information about event handling, see [Event Handlers Overview](../event-handlers-overview-windows-forms.md).</span></span>

<span data-ttu-id="7b3f1-128">Aşağıdaki yordamlarda, <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> ya da olayını kullanarak geçerli bir Doğum tarihinin nasıl test yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-128">The following procedures show how to test for a valid birth date using either the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> or the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span> <span data-ttu-id="7b3f1-129">Yordamlar, uygulama ayarlarınızı zaten oluşturmuş olduğunuz varsayımına göre yazılmıştır; Bu örnekte, adlı `DateOfBirth`bir ayar üzerinde sınır denetimi gerçekleştireceğiz.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-129">The procedures were written under the assumption that you have already created your application settings; in this example, we will perform bounds checking on a setting named `DateOfBirth`.</span></span> <span data-ttu-id="7b3f1-130">Ayarları oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Uygulama ayarları](how-to-create-application-settings.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-130">For more information about creating settings, see [How to: Create Application Settings](how-to-create-application-settings.md).</span></span>

### <a name="to-obtain-the-application-settings-object"></a><span data-ttu-id="7b3f1-131">Uygulama Ayarları nesnesini almak için</span><span class="sxs-lookup"><span data-stu-id="7b3f1-131">To obtain the application settings object</span></span>

- <span data-ttu-id="7b3f1-132">Aşağıdaki madde işaretli öğelerden birini tamamlayarak uygulama ayarları nesnesine (sarmalayıcı örneği) bir başvuru alın:</span><span class="sxs-lookup"><span data-stu-id="7b3f1-132">Obtain a reference to the application settings object (the wrapper instance) by completing one of the following bulleted items:</span></span>

  - <span data-ttu-id="7b3f1-133">Ayarlarınızı, **özellik düzenleyicisinde**Visual Studio uygulama ayarları iletişim kutusunu kullanarak oluşturduysanız, aşağıdaki ifade aracılığıyla diliniz için oluşturulan varsayılan ayarlar nesnesini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-133">If you created your settings using the Visual Studio Application Settings dialog box in the **Property Editor**, you can retrieve the default settings object generated for your language through the following expression.</span></span>

    ```csharp
    Configuration.Settings.Default
    ```

    ```vb
    MySettings.Default
    ```

    <span data-ttu-id="7b3f1-134">-veya-</span><span class="sxs-lookup"><span data-stu-id="7b3f1-134">-or-</span></span>

  - <span data-ttu-id="7b3f1-135">Visual Basic geliştiricisiyseniz ve proje tasarımcısını kullanarak uygulama ayarlarınızı oluşturduysanız, [My. Settings nesnesini](../../../visual-basic/language-reference/objects/my-settings-object.md)kullanarak ayarlarınızı alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-135">If you are a Visual Basic developer and you created your application settings using the Project Designer, you can retrieve your settings by using the [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>

    <span data-ttu-id="7b3f1-136">-veya-</span><span class="sxs-lookup"><span data-stu-id="7b3f1-136">-or-</span></span>

  - <span data-ttu-id="7b3f1-137">Ayarlarınızı <xref:System.Configuration.ApplicationSettingsBase> doğrudan türeterek oluşturduysanız, sınıfınızın el ile örneğini oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-137">If you created your settings by deriving from <xref:System.Configuration.ApplicationSettingsBase> directly, you need to instantiate your class manually.</span></span>

    ```csharp
    MyCustomSettings settings = new MyCustomSettings();
    ```

    ```vb
    Dim Settings as New MyCustomSettings()
    ```

<span data-ttu-id="7b3f1-138">Aşağıdaki yordamlar, bu yordamdaki son madde işaretli öğeyi tamamlayarak uygulama ayarları nesnesinin elde edildiği varsayımına göre yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-138">The following procedures were written under the assumption that the application settings object was obtained by completing the last bulleted item in this procedure.</span></span>

### <a name="to-validate-application-settings-when-a-setting-is-changing"></a><span data-ttu-id="7b3f1-139">Bir ayar değiştirilirken uygulama ayarlarını doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="7b3f1-139">To validate Application Settings when a setting is changing</span></span>

1. <span data-ttu-id="7b3f1-140">C# Geliştiriciyseniz, formunuzda veya denetiminizin `Load` olayında olay için <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> bir olay işleyicisi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-140">If you are a C# developer, in your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>

    <span data-ttu-id="7b3f1-141">-veya-</span><span class="sxs-lookup"><span data-stu-id="7b3f1-141">-or-</span></span>

    <span data-ttu-id="7b3f1-142">Visual Basic geliştiriciyseniz, `Settings` `WithEvents` anahtar sözcüğünü kullanarak değişkeni bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-142">If you are a Visual Basic developer, you should declare the `Settings` variable using the `WithEvents` keyword.</span></span>

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

2. <span data-ttu-id="7b3f1-143">Olay işleyicisini tanımlayın ve bu kodun içinde, Doğum tarihinde sınır denetimi yapmak için kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-143">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>

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

### <a name="to-validate-application-settings-when-a-save-occurs"></a><span data-ttu-id="7b3f1-144">Bir kaydetme gerçekleştiğinde uygulama ayarlarını doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="7b3f1-144">To validate Application Settings when a Save occurs</span></span>

1. <span data-ttu-id="7b3f1-145">Formunuzda veya denetiminizin `Load` olayında, <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> olay için bir olay işleyicisi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-145">In your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span>

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

2. <span data-ttu-id="7b3f1-146">Olay işleyicisini tanımlayın ve bu kodun içinde, Doğum tarihinde sınır denetimi yapmak için kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-146">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7b3f1-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b3f1-147">See also</span></span>

- [<span data-ttu-id="7b3f1-148">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7b3f1-148">Creating Event Handlers in Windows Forms</span></span>](../creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="7b3f1-149">Nasıl yapılır: Uygulama ayarları oluştur</span><span class="sxs-lookup"><span data-stu-id="7b3f1-149">How to: Create Application Settings</span></span>](how-to-create-application-settings.md)
