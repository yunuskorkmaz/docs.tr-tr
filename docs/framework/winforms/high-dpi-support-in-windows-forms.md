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
ms.openlocfilehash: 2c591aa19a13af2f5b38c46a886b8e0ee2f76c38
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540656"
---
# <a name="high-dpi-support-in-windows-forms"></a>Windows Forms'ta yüksek DPI desteği

.NET Framework 4.7 ile başlayarak, Windows Forms ortak yüksek DPI ve dinamik DPI senaryoları için geliştirmeler içerir. Bu güncelleştirmeler şunlardır: 

- Gibi ölçeklendirme ve düzen çok sayıda Windows Forms denetimleri <xref:System.Windows.Forms.MonthCalendar> denetimi ve <xref:System.Windows.Forms.CheckedListBox> denetimi. 

- Tek-geçişi ölçeklendirme.  .NET Framework 4.6 ve önceki sürümlerinde, ölçeklendirme, gerekli birden ölçeklendirilmesi bazı denetimler neden birden çok geçer gerçekleştirildi.

- Bir Windows Forms uygulaması başlatıldıktan sonra kullanıcı DPI veya ölçek faktörü değişiklik dinamik DPI senaryolar için destek.

.NET Framework 4.7 ile başlayan .NET Framework sürümlerinde geliştirilmiş yüksek DPI desteği bir katılım özelliğidir. Uygulamanızı yararlanmak için yapılandırmanız gerekir.

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>Windows Forms uygulamanızı yüksek DPI desteği için yapılandırma

Yüksek DPI tanıma destekleyen yeni bir Windows Forms özellikler, .NET Framework 4.7 hedefleyen ve Windows 10 Creators güncelleştirmesi ile başlayarak Windows işletim sistemleri üzerinde çalışan uygulamalarda kullanılabilir. 

Ayrıca, Windows Forms uygulaması'nda yüksek DPI desteği yapılandırmak için aşağıdakileri yapmanız gerekir:

- Windows 10 ile uyumluluğunu bildirin.

  Bunu yapmak için bildirim dosyasına aşağıdakileri ekleyin:

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- İzleyici başına DPI tanıma etkinleştirme *app.config* dosya.

  Yeni bir Windows Forms tanıtır [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md) yeni özellikler ve .NET Framework 4.7 ile başlayan eklenen özelleştirmeleri desteklemek için öğesi. Yüksek DPI desteği yeni özelliklerden yararlanmak için uygulama yapılandırma dosyasına aşağıdakileri ekleyin.   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > Önceki .NET Framework sürümlerinde, bildirim yüksek DPI desteği eklemek için kullanılır. Bu app.config dosyası üzerinde tanımlanan ayarları geçersiz kıldığından bu yaklaşım artık önerilir.
   
- Statik çağrı <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi.
   
  Bu, uygulama giriş noktası ilk yöntem çağrısında olmalıdır. Örneğin:
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>Yüksek DPI özellikleri dışında tek tek seçim yapma

Ayarı `DpiAwareness` değerini `PerMonitorV2` .NET Framework 4.7 ile başlayan .NET Framework sürümleri tarafından desteklenen tüm yüksek DPI tanıma özelliklerini etkinleştirir. Genellikle bu çoğu Windows Forms uygulamaları için yeterli olur. Ancak, bir veya daha fazla tek tek özellikler dışında bırakmak isteyebilirsiniz. Bunu yapmak için en önemli nedeni, var olan uygulama kodunuzun bu özelliği işlediğini olmasıdır.  Örneğin, uygulamanız otomatik ölçeklendirme işliyorsa, otomatik yeniden boyutlandırma özelliği gibi devre dışı bırakmak isteyebilirsiniz:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

Tek tek anahtarları ve değerleri listesi için bkz. [Windows Forms ekleme yapılandırma öğesi](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).

## <a name="new-dpi-change-events"></a>Yeni DPI değişikliği olayları

.NET Framework 4.7 ile başlayarak, üç yeni olaylar, program aracılığıyla dinamik DPI değişiklikleri işlemek izin ver:

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, bir denetim için DPI ayarı programlı olarak DPI değişiklik olayı için onun üst denetim sonra değiştirildi veya form oluştu tetiklendi.
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, bir denetim için DPI ayarı programlı olarak DPI değişiklik olayı için üst denetim önce değiştirildi veya form oluştu tetiklendi.
- <xref:System.Windows.Forms.Form.DpiChanged>, formu şu anda görüntüleyen görüntü cihazında DPI ayarını değiştirdiğinde tetiklenen.

## <a name="new-helper-methods-and-properties"></a>Yeni yardımcı yöntemler ve Özellikler

.NET Framework 4.7, çok sayıda yeni yardımcı yöntemler ve DPI ölçeklendirme hakkında bilgi sağlar ve DPI ölçeklendirme gerçekleştirmenize olanak sağlayan özellikleri de ekler. Bu güncelleştirmeler şunlardır:

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, dönüştüren bir değerini mantıksal ağdan cihaz piksel.

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, bir cihaz için mantıksal DPI bir bit eşlem görüntüsüne ölçeklendirir.

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>, geçerli cihaz için DPI değeri döndürür.

## <a name="versioning-considerations"></a>Sürüm oluşturma konuları

.NET Framework 4.7 ve Windows 10 Creators Update çalıştıran ek olarak, uygulamanızın içinde yüksek DPI geliştirmeleri ile uyumlu olmayan bir ortamda da çalıştırabilirsiniz. Bu durumda, bir geri dönüş için uygulamanızı geliştirmek gerekir. Bunu gerçekleştirmek için yapabilirsiniz [özel çizim](./controls/user-drawn-controls.md) ölçeklendirme işlemek için.

Bunu yapmak için aynı zamanda uygulamanızın üzerinde çalıştığı işletim sistemi belirlemeniz gerekir. Bunu aşağıdaki gibi kod ile yapabilirsiniz:

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

Uygulama bildiriminde desteklenen bir işletim sistemi olarak listelenen değildi, uygulamanız başarıyla Windows 10 algılamaz unutmayın.

Ayrıca, uygulamanın derlendiği .NET Framework sürümünü kontrol edebilirsiniz:

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms yapılandırma öğesi Ekle](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [Windows Forms Boyutunu ve Ölçeğini Ayarlama](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)
