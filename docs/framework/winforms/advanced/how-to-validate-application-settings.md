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
ms.openlocfilehash: b7aba4935756fc218a1fadaa1dd9f20a5bc3034f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317900"
---
# <a name="how-to-validate-application-settings"></a>Nasıl yapılır: Uygulama Ayarlarını Doğrulama
Bu konuda, kalıcı önce uygulama ayarlarını doğrulama gösterilmiştir.  
  
 Uygulama ayarları kesin olarak belirlenmiştir, kullanıcılar için belirli bir ayarı yanlış türde veri atanamaz bazı güvenle sahip. Ancak, bir kullanıcı hala kabul edilebilir sınırları dışında kalan bir ayar için bir değer atamak denemiş olabilir — örneğin, gelecekte gerçekleşen bir doğum tarihi sağlama. <xref:System.Configuration.ApplicationSettingsBase>, üst sınıfı sınıflarının tüm uygulama ayarları, bu sınır denetimini etkinleştirmek için dört olayları gösterir. Bu olayları işleme doğrulama kodunuzun tamamını proje boyunca Saçılma yerine tek bir konuma yerleştirir.  
  
 Aşağıdaki tabloda açıklandığı gibi ayarlarınızı doğrulamak ihtiyacınız olduğunda kullandığınız olay bağlıdır.  
  
|Olay|Yinelenme ve kullanın|  
|-----------|------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|Ayarlar özellik grubu ilk yüklemesinden sonra gerçekleşir.<br /><br /> Uygulama içinde kullandıkları önce tüm özellik grubunun ilk değerlerini doğrulamak için bu olayı kullanın.|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|Bir tek ayarları özelliğinin değeri değiştirildikten hemen önce gerçekleşir.<br /><br /> Tek bir özellik, değiştirilmeden önceki doğrulamak için bu olayı kullanın. Kullanıcılar kendi Eylemler ve seçenekler ile ilgili anında geri bildirim sunabilir.|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|Bir çoklu ayarları özelliğinin değeri değiştikten sonra gerçekleşir.<br /><br /> Tek bir özellik, değiştirildikten sonra doğrulamak için bu olayı kullanın. Uzun, zaman uyumsuz doğrulama işlemi gerekli olmadığı sürece bu olay için doğrulama nadiren kullanılır.|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|Ayarlar özellik grubunu depolanmadan önce gerçekleşir.<br /><br /> Kalıcı önce grubunun tüm özellik değerlerini doğrulamak için bu olayı kullanın diske.|  
  
 Genellikle, bu olayların aynı uygulama içindeki tüm doğrulama amacıyla kullanmaz. Örneğin, genellikle yalnızca işleyerek tüm doğrulama gereksinimlerini karşılamak mümkündür <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> olay.  
  
 Geçersiz bir değer algıladığında bir olay işleyicisi genellikle aşağıdaki eylemlerden birini gerçekleştirir:  
  
-   Otomatik olarak varsayılan değer gibi doğru olduğu bilinen bir değer sağlar.  
  
-   Bilgi için sunucu kodu kullanıcısı yeniden sorgular.  
  
-   Önce ilişkili eylemlerinin, gibi harekete geçirilen olayları <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> ve <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, kullandığı <xref:System.ComponentModel.CancelEventArgs> işlemi iptal etmek için bağımsız değişken.  
  
 Olay işleme hakkında daha fazla bilgi için bkz. [olay işleyicilerine genel bakış](../event-handlers-overview-windows-forms.md).  
  
 Aşağıdaki yordamlardan herhangi birini kullanarak geçerli bir doğum tarihi için test etme Göster <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> veya <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> olay. Yordamları, uygulama ayarlarınızı oluşturduysanız varsayım altında yazılmıştır; Bu örnekte biz sınır adlı ayarda denetimi gerçekleştirir `DateOfBirth`. Ayarları oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Uygulama ayarları oluşturma](how-to-create-application-settings.md).  
  
### <a name="to-obtain-the-application-settings-object"></a>Uygulama Ayarları nesnesini almak için  
  
-   Uygulama Ayarları nesnesini (sarmalayıcı örnek) başvuru aşağıdaki madde işaretli öğelerden birini tamamlayarak alın:  
  
    -   Visual Studio uygulama ayarları iletişim kutusunda kullanarak ayarlarınızı oluşturduysanız **Özellik Düzenleyici**, dil ifadesini aracılığıyla oluşturulan varsayılan ayarları nesnesi alabilirsiniz.  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         -veya-  
  
    -   Visual Basic Geliştirici ve uygulama ayarlarınızı, Proje Tasarımcısı'nı kullanarak oluşturduğunuz kullanarak ayarlarınızı alabilirsiniz [My.Settings nesnesi](~/docs/visual-basic/language-reference/objects/my-settings-object.md).  
  
         -veya-  
  
    -   Ayarlarınızı türeterek oluşturduysanız <xref:System.Configuration.ApplicationSettingsBase> doğrudan sınıfınıza el ile oluşturmak ihtiyacınız.  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 Aşağıdaki yordamlar son madde işaretli öğesinde bu yordamı izleyerek uygulamanın ayarlar nesnesi edinilen varsayımı yazılmıştır.  
  
### <a name="to-validate-application-settings-when-a-setting-is-changing"></a>Bir ayarı değiştirirken uygulama ayarlarını doğrulamak için  
  
1. Eğer bir C# geliştirici, form veya Denetim `Load` olayı için bir olay işleyicisi ekleme <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> olay.  
  
     -veya-  
  
     Visual Basic Geliştirici olup, size bildirmelidir `Settings` değişken kullanarak `WithEvents` anahtar sözcüğü.  
  
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
  
2. Olay işleyicisi tanımlama ve içinde sınır doğum tarihi denetimi gerçekleştirmek için kod yazın.  
  
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
  
### <a name="to-validate-application-settings-when-a-save-occurs"></a>Kaydetme, uygulama ayarlarını doğrulamak için gerçekleşir.  
  
1. Form veya Denetim `Load` olayı için olay işleyicisi eklemek <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> olay.  
  
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
  
2. Olay işleyicisi tanımlama ve içinde sınır doğum tarihi denetimi gerçekleştirmek için kod yazın.  
  
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
- [Nasıl yapılır: Uygulama ayarları oluşturma](how-to-create-application-settings.md)
