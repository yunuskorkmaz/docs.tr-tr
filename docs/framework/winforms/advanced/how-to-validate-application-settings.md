---
title: "Nasıl yapılır: Uygulama Ayarlarını Doğrulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating application settings
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], validating
ms.assetid: 9f145ada-4267-436a-aa4c-c4dcffd0afb7
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 309429c2481bad3a8dff4708d9e2ea8a03057a4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-application-settings"></a>Nasıl yapılır: Uygulama Ayarlarını Doğrulama
Bu konu, kalıcı yapılan önce uygulama ayarlarını doğrulama gösterilmiştir.  
  
 Uygulama ayarları kesin türü belirtilmiş olduğundan, kullanıcılar için belirli bir ayarı yanlış türde veri atayamazsınız bazı size güven verir. Ancak, kullanıcı hala kabul edilebilir sınırların dışında kalan bir ayar için bir değer atamaya deneyebilir — Örneğin, gelecekte oluşan bir doğum tarihi sağlama. <xref:System.Configuration.ApplicationSettingsBase>, tüm uygulama ayarlarını sınıfları, üst sınıfının denetimi gibi sınırları etkinleştirmek için dört olayları gösterir. Bu olayları işleme tüm doğrulama kodunuzu boyunca projenizin Saçılma yerine tek bir konuma yerleştirir.  
  
 Aşağıdaki tabloda açıklandığı gibi ayarlarınızı doğrulamanıza gerektiğinde, kullandığınız olay bağlıdır.  
  
|Olay|Geçişi ve kullanımı|  
|-----------|------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|Ayarlar özellik grubu ilk yüklemeden sonra oluşur.<br /><br /> Bu olay, uygulama içinde kullanılmadan önce tüm özellik grubu için başlangıç değerlerini doğrulamak için kullanın.|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|Bir tek ayarları özelliğinin değeri değiştirilmeden önce gerçekleşir.<br /><br /> Bu olay, değiştirilmeden önce tek bir özellik doğrulamak için kullanın. Kullanıcılar kendi eylemleri ve seçenekler ile ilgili anında geri bildirim sağlayabilirsiniz.|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|Bir tek ayarları özelliğinin değeri değiştikten sonra gerçekleşir.<br /><br /> Bu olay, değiştirildikten sonra tek bir özellik doğrulamak için kullanın. Uzun ve zaman uyumsuz doğrulama işlemi gerekli olmadığı sürece bu olay için doğrulama nadiren kullanılır.|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|Ayarlar özellik grubunda depolanan önce gerçekleşir.<br /><br /> Kalıcı yapılan önce tüm özellik grubunun değerlerini doğrulamak için bu olayı kullanın diske.|  
  
 Tipik olarak, tüm bu olayları aynı uygulamadaki doğrulama amacıyla kullanmaz. Örneğin, genellikle yalnızca işleyerek tüm doğrulama gereksinimlerini karşılamak mümkündür <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> olay.  
  
 Geçersiz bir değer algıladığında, olay işleyici genellikle aşağıdaki eylemlerden birini gerçekleştirir:  
  
-   Otomatik olarak gibi varsayılan değeri doğru olması için bilinen bir değerini sağlar.  
  
-   Bilgi için sunucu kodu kullanıcı yeniden sorgular.  
  
-   İlişkili eylemlerinin önce aşağıdaki gibi başlatılan olayları için <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> ve <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, kullanan <xref:System.ComponentModel.CancelEventArgs> işlemi iptal etmek için bağımsız değişken.  
  
 Olay işleme hakkında daha fazla bilgi için bkz: [olay işleyicilerine genel bakış](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
 Aşağıdaki yordamları kullanarak geçerli doğum tarihini test etme Göster <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> veya <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> olay. Yordamlar, uygulamanızın ayarlarını önceden oluşturduğunuz varsayım altında yazılmış; Bu örnekte, adlı bir ayarda denetimi sınırları gerçekleştiririz `DateOfBirth`. Ayarları oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: uygulama ayarları oluştur](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
### <a name="to-obtain-the-application-settings-object"></a>Uygulama Ayarları nesnesini almak için  
  
-   Uygulama Ayarları nesnesini (sarmalayıcı örneği) referansı aşağıdaki madde işaretli öğelerden birini tamamlayarak alın:  
  
    -   Visual Studio uygulama ayarları iletişim kutusunda kullanarak ayarlarınızı oluşturduysanız **Özellik Düzenleyici**, dilinizi ifadesini aracılığıyla oluşturulan varsayılan ayarları nesnesi alabilirsiniz.  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         veya  
  
    -   Visual Basic Geliştirici misiniz ve uygulama ayarlarınızı, Proje Tasarımcısı'nı kullanarak oluşturduğunuz, kullanarak ayarlarınızı alabilirsiniz [My.Settings nesnesi](~/docs/visual-basic/language-reference/objects/my-settings-object.md).  
  
         veya  
  
    -   Türetme tarafından ayarlarınızı oluşturduysanız <xref:System.Configuration.ApplicationSettingsBase> doğrudan sınıfınız el ile örneği gerekir.  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 Aşağıdaki yordamlar, uygulama ayarları nesnesi bu yordam son madde işaretli öğenin tamamlayarak edinilen varsayımına altında yazılmıştır.  
  
### <a name="to-validate-application-settings-when-a-setting-is-changing"></a>Bir ayarı değiştirirken uygulama ayarlarını doğrulamak için  
  
1.  C# Geliştirici, form veya denetimin olup olmadığını `Load` olayı için bir olay işleyicisi ekleme <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> olay.  
  
     veya  
  
     Visual Basic Geliştirici olup, bildirmelidir `Settings` değişken kullanarak `WithEvents` anahtar sözcüğü.  
  
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
  
2.  Olay işleyicisi tanımlama ve içinde sınırları doğum tarihi denetimi gerçekleştirmek için kod yazma.  
  
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
  
### <a name="to-validate-application-settings-when-a-save-occurs"></a>Uygulama ayarları kaydetme zaman doğrulamak için oluşur  
  
1.  Form veya denetimin `Load` olayı için bir olay işleyicisi ekleme <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> olay.  
  
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
  
2.  Olay işleyicisi tanımlama ve içinde sınırları doğum tarihi denetimi gerçekleştirmek için kod yazma.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'ta olay işleyicileri oluşturma](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Nasıl yapılır: uygulama ayarları oluştur](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)
