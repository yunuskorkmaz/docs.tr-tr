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
# <a name="how-to-validate-application-settings"></a>Nasıl yapılır: Uygulama Ayarlarını Doğrulama

Bu konuda, uygulama ayarlarının kalıcı olmadan önce nasıl doğrulanacağı gösterilmektedir.

Uygulama ayarları kesin olarak yazıldığından, kullanıcıların yanlış türde verileri belirli bir ayara atayamadığı bazı güvenlerdir. Bununla birlikte, bir Kullanıcı, kabul edilebilir sınırların dışında kalan bir ayara bir değer atamayı deneyebilir (örneğin, gelecekte oluşan bir Doğum tarihi sağlama). <xref:System.Configuration.ApplicationSettingsBase>Tüm uygulama ayarları sınıflarının üst sınıfı, bu tür sınırlar denetimini etkinleştirmek için dört olay sunar. Bu olayları işlemek, tüm doğrulama kodunuzu projeniz genelinde saçmak yerine tek bir konuma koyar.

Kullandığınız olay, aşağıdaki tabloda açıklandığı gibi ayarlarınızı doğrulamanız gerektiğinde değişir.

|Olay|Oluşum ve kullanım|
|-----------|------------------------|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|Bir ayarlar özellik grubunun ilk yüklemesiyle sonra oluşur.<br /><br /> Uygulama içinde kullanılmadan önce tüm özellik grubunun başlangıç değerlerini doğrulamak için bu olayı kullanın.|
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|Tek bir Settings özelliğinin değeri değiştirilmeden önce oluşur.<br /><br /> Değiştirilmeden önce tek bir özelliği doğrulamak için bu olayı kullanın. Bu, kullanıcılara eylemlerle ve seçimleriyle ilgili anında geri bildirim sağlayabilir.|
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|Tek bir Settings özelliğinin değeri değiştirildikten sonra gerçekleşir.<br /><br /> Değiştirildikten sonra tek bir özelliği doğrulamak için bu olayı kullanın. Bu olay, daha uzun bir zaman uyumsuz doğrulama işlemi gerekli olmadığı sürece doğrulama için nadiren kullanılır.|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|Ayarlar özellik grubu depolanmadan önce oluşur.<br /><br /> Tüm özellik grubu değerlerini diske kalıcı yapmadan önce doğrulamak için bu olayı kullanın.|

Genellikle, doğrulama amacıyla aynı uygulama içinde bu olayların tümünü kullanamazsınız. Örneğin, genellikle yalnızca <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> olayını işleyerek tüm doğrulama gereksinimlerinin yerine getirilmesi mümkündür.

Bir olay işleyicisi, geçersiz bir değer algıladığında, genellikle aşağıdaki eylemlerden birini gerçekleştirir:

- , Varsayılan değer gibi, doğru olarak bilinen bir değeri otomatik olarak sağlar.

- Bilgi için sunucu kodu kullanıcısını yeniden sorgular.

- <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> <xref:System.ComponentModel.CancelEventArgs> Ve gibiilişkilieylemlerindenönceoluşturulanolaylariçin,işlemiiptaletmekiçinbağımsızdeğişkeninikullanır.<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>

Olay işleme hakkında daha fazla bilgi için bkz. [olay Işleyicilerine genel bakış](../event-handlers-overview-windows-forms.md).

Aşağıdaki yordamlarda, <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> ya da olayını kullanarak geçerli bir Doğum tarihinin nasıl test yapılacağı gösterilmektedir. Yordamlar, uygulama ayarlarınızı zaten oluşturmuş olduğunuz varsayımına göre yazılmıştır; Bu örnekte, adlı `DateOfBirth`bir ayar üzerinde sınır denetimi gerçekleştireceğiz. Ayarları oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Uygulama ayarları](how-to-create-application-settings.md)oluşturun.

### <a name="to-obtain-the-application-settings-object"></a>Uygulama Ayarları nesnesini almak için

- Aşağıdaki madde işaretli öğelerden birini tamamlayarak uygulama ayarları nesnesine (sarmalayıcı örneği) bir başvuru alın:

  - Ayarlarınızı, **özellik düzenleyicisinde**Visual Studio uygulama ayarları iletişim kutusunu kullanarak oluşturduysanız, aşağıdaki ifade aracılığıyla diliniz için oluşturulan varsayılan ayarlar nesnesini alabilirsiniz.

    ```csharp
    Configuration.Settings.Default
    ```

    ```vb
    MySettings.Default
    ```

    -veya-

  - Visual Basic geliştiricisiyseniz ve proje tasarımcısını kullanarak uygulama ayarlarınızı oluşturduysanız, [My. Settings nesnesini](../../../visual-basic/language-reference/objects/my-settings-object.md)kullanarak ayarlarınızı alabilirsiniz.

    -veya-

  - Ayarlarınızı <xref:System.Configuration.ApplicationSettingsBase> doğrudan türeterek oluşturduysanız, sınıfınızın el ile örneğini oluşturmanız gerekir.

    ```csharp
    MyCustomSettings settings = new MyCustomSettings();
    ```

    ```vb
    Dim Settings as New MyCustomSettings()
    ```

Aşağıdaki yordamlar, bu yordamdaki son madde işaretli öğeyi tamamlayarak uygulama ayarları nesnesinin elde edildiği varsayımına göre yazılmıştır.

### <a name="to-validate-application-settings-when-a-setting-is-changing"></a>Bir ayar değiştirilirken uygulama ayarlarını doğrulamak için

1. C# Geliştiriciyseniz, formunuzda veya denetiminizin `Load` olayında olay için <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> bir olay işleyicisi ekleyin.

    -veya-

    Visual Basic geliştiriciyseniz, `Settings` `WithEvents` anahtar sözcüğünü kullanarak değişkeni bildirmeniz gerekir.

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

2. Olay işleyicisini tanımlayın ve bu kodun içinde, Doğum tarihinde sınır denetimi yapmak için kodu yazın.

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

### <a name="to-validate-application-settings-when-a-save-occurs"></a>Bir kaydetme gerçekleştiğinde uygulama ayarlarını doğrulamak için

1. Formunuzda veya denetiminizin `Load` olayında, <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> olay için bir olay işleyicisi ekleyin.

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

2. Olay işleyicisini tanımlayın ve bu kodun içinde, Doğum tarihinde sınır denetimi yapmak için kodu yazın.

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

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Olay İşleyicileri Oluşturma](../creating-event-handlers-in-windows-forms.md)
- [Nasıl yapılır: Uygulama ayarları oluştur](how-to-create-application-settings.md)
