---
title: Yüksek DPı desteği
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
ms.openlocfilehash: a5c3125475c2de2cf83a3d97e356b26c0acdde99
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741890"
---
# <a name="high-dpi-support-in-windows-forms"></a>Windows Forms yüksek DPı desteği

.NET Framework 4,7 ' den başlayarak, Windows Forms genel yüksek DPı ve dinamik DPı senaryolarına yönelik iyileştirmeler içerir. Bu güncelleştirmeler şunlardır:

- <xref:System.Windows.Forms.MonthCalendar> denetimi ve <xref:System.Windows.Forms.CheckedListBox> denetimi gibi bir dizi Windows Forms denetiminin ölçeklendirilmesine ve düzenine yönelik iyileştirmeler.

- Tek geçişli ölçekleme.  .NET Framework 4,6 ve önceki sürümlerde ölçekleme birden çok geçiş aracılığıyla gerçekleştirildi, bu da bazı denetimlerin gerekenden daha fazla ölçeklendirilmesine neden olur.

- Windows Forms bir uygulama başlatıldıktan sonra kullanıcının DPı veya ölçek faktörünü değiştirdiği dinamik DPı senaryoları için destek.

.NET Framework 4,7 ' den başlayarak .NET Framework sürümlerinde, gelişmiş yüksek DPı desteği, bir katılım özelliğidir. Uygulamanızı bundan faydalanmak için yapılandırmanız gerekir.

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>Windows Forms uygulamanızı yüksek DPı desteği için yapılandırma

Yüksek DPı tanımayı destekleyen yeni Windows Forms özellikleri yalnızca .NET Framework 4,7 ' i hedefleyen ve Windows 10 Creators Update ile başlayan Windows işletim sistemlerinde çalışan uygulamalarda kullanılabilir.

Ayrıca, Windows Forms uygulamanızda yüksek DPı desteğini yapılandırmak için aşağıdakileri yapmanız gerekir:

- Windows 10 ile uyumluluk bildirin.

  Bunu yapmak için bildirim dosyanıza aşağıdakileri ekleyin:

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- *App. config* dosyasında MONITÖR başına DPI tanımayı etkinleştirin.

  Windows Forms, .NET Framework 4,7 ile başlayarak eklenen yeni özellikleri ve özelleştirmeleri desteklemek için yeni bir [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) öğesi sunmaktadır. Yüksek DPı 'yi destekleyen yeni özelliklerden yararlanmak için, uygulama yapılandırma dosyanıza aşağıdakini ekleyin.

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > .NET Framework önceki sürümlerinde, yüksek DPı desteği eklemek için bildirimi kullandınız. Bu yaklaşım artık önerilmez, çünkü App. config dosyasında tanımlanan ayarları geçersiz kılar.

- Statik <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemini çağırın.

  Bu, uygulama giriş noktandaki ilk yöntem çağrısı olmalıdır. Örneğin:

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>Tek başına yüksek DPı özelliklerinden çıkma

`DpiAwareness` değerini `PerMonitorV2` olarak ayarlamak, .NET Framework sürümleri tarafından desteklenen tüm yüksek DPı tanıma özelliklerinin .NET Framework 4,7 ile başlatılmasını sağlar. Genellikle, bu çoğu Windows Forms uygulama için yeterlidir. Ancak, bir veya daha fazla ayrı özelliği devre dışı bırakmak isteyebilirsiniz. Bunu yapmanın en önemli nedeni, mevcut uygulama kodunuzun bu özelliği zaten işlemektir.  Örneğin, uygulamanız otomatik ölçeklendirmeyi işlediğinde, otomatik yeniden boyutlandırma özelliğini aşağıdaki gibi devre dışı bırakmak isteyebilirsiniz:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

Tek tek anahtarların ve değerlerinin listesi için bkz. [Windows Forms Configuration öğesi ekleme](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).

## <a name="new-dpi-change-events"></a>Yeni DPı değişiklik olayları

4,7 .NET Framework başlayarak, üç yeni olay dinamik DPı değişikliklerini programlı bir şekilde işleyebilsin:

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, bir denetimin DPı ayarı, onun üst denetimi veya formu için bir DPı değişiklik olayından sonra programlı olarak değiştirildiğinde harekete geçirilir.
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, bir denetimin DPı ayarı, üst denetimi veya formu için bir DPı değişiklik olayından önce programlı olarak değiştirildiğinde harekete geçirilir.
- <xref:System.Windows.Forms.Form.DpiChanged>, DPı ayarı formun görüntülenmekte olan görüntü cihazında değiştiğinde harekete geçirilir.

## <a name="new-helper-methods-and-properties"></a>Yeni yardımcı yöntemler ve Özellikler

.NET Framework 4,7 Ayrıca, DPı ölçeklendirme hakkında bilgi sağlayan ve DPı ölçeklendirme gerçekleştirmenize olanak tanıyan bir dizi yeni yardımcı yöntem ve özellik ekler. Bu güncelleştirmeler şunlardır:

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, bir değeri mantıksal olan cihazdan cihaz pikseline dönüştürür.

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, bir bit eşlem resmini bir cihaz için mantıksal DPı 'ye ölçeklendirir.

- geçerli cihaz için DPı 'yi döndüren <xref:System.Windows.Forms.Control.DeviceDpi%2A>.

## <a name="versioning-considerations"></a>Sürüm oluşturma konuları

.NET Framework 4,7 ve Windows 10 Creators Update üzerinde çalıştırmanın yanı sıra, uygulamanız da yüksek DPı geliştirmeleri ile uyumlu olmayan bir ortamda çalıştırılabilir. Bu durumda, uygulamanız için bir geri dönüş geliştirmeniz gerekir. Ölçeklendirmeyi işlemek için [özel çizim](./controls/user-drawn-controls.md) gerçekleştirmek üzere bunu yapabilirsiniz.

Bunu yapmak için uygulamanızın üzerinde çalıştığı işletim sistemini de belirlemeniz gerekir. Bunu aşağıdaki gibi kodla yapabilirsiniz:

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

Uygulamanızın, uygulama bildiriminde desteklenen bir işletim sistemi olarak listelenmediyse Windows 10 ' un başarıyla algılanmadığını unutmayın.

Ayrıca, uygulamanın oluşturulduğu .NET Framework sürümünü denetleyebilirsiniz:

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms yapılandırma öğesi Ekle](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [Windows Forms Boyutunu ve Ölçeğini Ayarlama](adjusting-the-size-and-scale-of-windows-forms.md)
