---
title: Windows Forms'ta yüksek DPI desteği
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbf2d7b61b34a2cd4641a77ee1f2fcdff7f3c3fe
ms.sourcegitcommit: b7763f3435635850a76d4cbcf09bdce6c019208a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34483547"
---
# <a name="high-dpi-support-in-windows-forms"></a>Windows Forms'ta yüksek DPI desteği

.NET Framework 4.7 ile başlayarak, Windows Forms ortak yüksek DPI ve dinamik DPI senaryoları için geliştirmeler içerir. Bu güncelleştirmeler şunlardır: 

- Gibi ölçekleme ve çok sayıda Windows Forms düzeni geliştirmeler denetimleri <xref:System.Windows.Forms.MonthCalendar> denetim ve <xref:System.Windows.Forms.CheckedListBox> denetim. 

- Tek ölçeklendirme geçiş.  .NET Framework 4.6 ve önceki sürümlerinde ölçeklendirme hangi ölçeklendirilmesi için bazı denetimler neden birden çok gerekli birden çok geçer gerçekleştirildi.

- Bir Windows Forms uygulaması başlatıldıktan sonra kullanıcı DPI veya ölçek faktörü değişiklikleri dinamik DPI senaryolar için destek.

.NET Framework 4.7 ile başlayan .NET Framework sürümlerinde, Gelişmiş yüksek DPI destek bir katılımı özelliğidir. Bunu yararlanmak için uygulamanızı yapılandırmanız gerekir.

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>Windows Forms uygulamanız yüksek DPI desteği için yapılandırma

Yüksek DPI tanıma desteği yeni Windows Forms özellikleri, .NET Framework 4.7 hedefleyen ve Windows 10 oluşturucuları güncelleştirmesi ile başlayarak Windows işletim sistemlerinde çalışan uygulamalarda kullanılabilir. 

Ayrıca, Windows Forms uygulaması'nda yüksek DPI desteğini yapılandırmak için aşağıdakileri yapmanız gerekir:

- Windows 10 ile uyumluluk bildirin.

  Bunu yapmak için bildirim dosyanızı aşağıdakileri ekleyin:

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- İzleyici başına DPI tanıma etkinleştirmek *app.config* dosya.

  Yeni bir Windows Forms tanıtır [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md) öğesinde yeni özellikler ve .NET Framework 4.7 ile başlayan eklenen özelleştirmeleri desteklemek için. Yüksek DPI destekleyen yeni özelliklerden yararlanmak için aşağıdaki uygulama yapılandırma dosyasına ekleyin.   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > .NET Framework önceki sürümlerde bildirim yüksek DPI desteği eklemek için kullanılır. App.config dosyasını tanımlanan ayarları geçersiz kılar gerektiğinden bu yaklaşım artık önerilir.
   
- Statik çağrı <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi.
   
  Bu uygulama giriş noktası ilk yöntem çağrısında olmalıdır. Örneğin:
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>Yüksek DPI özellikleri dışında tek tek kullanmama

Ayarı `DpiAwareness` değeri `PerMonitorV2` ile .NET Framework 4.7 başlangıç .NET Framework sürümleri tarafından desteklenen tüm yüksek DPI tanıma özellikleri etkinleştirir. Genellikle, bu çoğu Windows Forms uygulamaları için yeterlidir. Ancak, bir veya daha fazla tek tek özellikleri dışında opt isteyebilirsiniz. Bunu yapmak için en önemli varolan uygulama kodunuz zaten bu özelliği işler nedenidir.  Örneğin, uygulamanız otomatik ölçeklendirme işliyorsa, otomatik yeniden boyutlandırma özelliğini aşağıdaki gibi devre dışı bırakmak isteyebilirsiniz:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

Tek tek anahtarları ve değerleri listesi için bkz: [Windows Forms eklemek yapılandırma öğesi](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).

## <a name="new-dpi-change-events"></a>Yeni DPI değişikliği olayları

.NET Framework 4.7 ile başlayarak, üç yeni olaylar, program aracılığıyla dinamik DPI değişiklikleri işlemeye izin ver:

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, bir denetim için DPI ayarı program aracılığıyla, üst denetim için bir DPI değişikliği olayından sonra değiştirilir veya form oluştu tetiklenir.
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, bir denetim için DPI ayarı program aracılığıyla bir DPI değişiklik olayı, üst denetim için önce değiştirilmiş ya da form oluştu tetiklenir.
- <xref:System.Windows.Forms.Form.DpiChanged>, DPI ayarı formun şu anda görüntülendiği görüntü cihazında değiştiğinde tetiklenir.

## <a name="new-helper-methods-and-properties"></a>Yeni yardımcı yöntemler ve Özellikler

.NET Framework 4.7 bir dizi yeni yardımcı yöntemler ve DPI ölçeklendirme hakkında bilgi sağlar ve DPI ölçeklendirme gerçekleştirmenize olanak sağlayan özellikleri de ekler. Bu güncelleştirmeler şunlardır:

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, dönüştüren bir değerini mantıksal ağdan aygıt pikselleri.

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, bir cihaz için mantıksal DPI bitmap görüntüye ölçeklendirir.

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>, geçerli cihazınız için DPI döndürür.

## <a name="versioning-considerations"></a>Sürüm oluşturma konuları

.NET Framework 4.7 ve Windows 10 oluşturucuları Update çalıştırmanın yanı sıra, uygulamanızın hangi yüksek DPI geliştirmelerle uyumlu olmayan bir ortamda de çalıştırabilirsiniz. Bu durumda, uygulamanız için bir geri dönüş geliştirmek gerekir. Bunu gerçekleştirmek için yapabilirsiniz [özel çizim](./controls/user-drawn-controls.md) ölçeklendirme işlemek için.

Bunu yapmak için Ayrıca, uygulamanızın üzerinde çalıştığı işletim sisteminin belirlemekte gerekir. Bunu aşağıdaki gibi kod ile yapabilirsiniz:

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

Uygulama bildiriminde desteklenen bir işletim sistemi olarak listelenen değildi uygulamanız başarıyla Windows 10 algılamaz unutmayın.

Uygulama karşı oluşturulmuş .NET Framework sürümünü de denetleyebilirsiniz:

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>Ayrıca bkz.

[Windows Forms yapılandırma öğesi Ekle](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)  
[Windows Forms Boyutunu ve Ölçeğini Ayarlama](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)
