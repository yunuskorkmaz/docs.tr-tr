---
title: PrintPreviewDialog Denetimine Genel Bakış (Windows Forms)
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
ms.openlocfilehash: 670886956e1b348895862c117ccf9cf586bde8bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141224"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>Printönizleme Iletişim kutusu denetimine genel bakış (Windows Forms)

Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> denetimi, yazdırıldığında bir [PrintDocument](printdocument-component-windows-forms.md) 'ın nasıl görüneceğini göstermek için kullanılan önceden yapılandırılmış bir iletişim kutusudur. Kendi iletişim kutusunu yapılandırmak yerine, bunu Windows tabanlı uygulamanızda basit bir çözüm olarak kullanın. Denetim, yazdırma, yakınlaştırma, bir veya birden çok sayfa görüntüleme ve iletişim kutusunu kapatma düğmelerini içerir.

## <a name="key-properties-and-methods"></a>Anahtar özellikleri ve yöntemleri

Denetimin anahtar özelliği, belgeyi önizlenen olarak ayarlayan <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>. Belge bir <xref:System.Drawing.Printing.PrintDocument> nesnesi olmalıdır. İletişim kutusunu göstermek için <xref:System.Windows.Forms.Form.ShowDialog%2A> yöntemini çağırmanız gerekir. Kenar yumuşatma, metnin daha düzgün görünmesine neden olabilir, ancak aynı zamanda ekranı daha yavaş hale getirir; kullanmak için <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> özelliğini `true`olarak ayarlayın.

Bazı özellikler <xref:System.Windows.Forms.PrintPreviewDialog> içeren <xref:System.Windows.Forms.PrintPreviewControl> ile kullanılabilir. (Bu <xref:System.Windows.Forms.PrintPreviewControl> forma eklemeniz gerekmez; iletişim kutusunu formunuza eklediğinizde otomatik olarak <xref:System.Windows.Forms.PrintPreviewDialog> içinde yer alır.) <xref:System.Windows.Forms.PrintPreviewControl> aracılığıyla kullanılabilen özelliklerin örnekleri, denetimde yatay ve dikey olarak görüntülenen sayfa sayısını belirleyen <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> ve <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> özelliklerdir. <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> özelliğine Visual Basic, görselde C#`printPreviewDialog1.PrintPreviewControl.Columns` veya görselde C++`printPreviewDialog1->PrintPreviewControl->Columns` `PrintPreviewDialog1.PrintPreviewControl.Columns` olarak erişebilirsiniz.

## <a name="printpreviewdialog-performance"></a>Printönizleme Iletişim kutusu performansı

Aşağıdaki koşullarda <xref:System.Windows.Forms.PrintPreviewDialog> denetimi çok yavaş başlatılır:

- Bir ağ yazıcısı kullanılır.
- Bu yazıcı için çift yönlü ayarlar gibi Kullanıcı tercihleri değiştirilir.

.NET Framework 4.5.2 üzerinde çalışan uygulamalar için, <xref:System.Windows.Forms.PrintPreviewDialog> denetimi başlatma performansını geliştirmek için yapılandırma dosyanızın \<appSettings > bölümüne aşağıdaki anahtarı ekleyebilirsiniz:

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

`EnablePrintPreviewOptimization` anahtarı başka bir değere ayarlandıysa veya anahtar yoksa, iyileştirme uygulanmaz.

.NET Framework 4,6 veya sonraki sürümlerde çalışan uygulamalar için, uygulama yapılandırma dosyanızın [\<runtime >](../../configure-apps/file-schema/runtime/index.md) bölümünde yer alan [\<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesine aşağıdaki anahtarı ekleyebilirsiniz:

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

Anahtar yoksa veya başka bir değere ayarlandıysa, iyileştirme uygulanmaz.

Yazıcı ayarlarını değiştirmek için <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> olayını kullanırsanız, bir iyileştirme yapılandırma anahtarı ayarlanmış olsa bile <xref:System.Windows.Forms.PrintPreviewDialog> denetiminin performansı geliştirilecektir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [PrintPreviewControl Denetimine Genel Bakış](printpreviewcontrol-control-overview-windows-forms.md)
- [PrintPreviewDialog Denetimi](printpreviewdialog-control-windows-forms.md)
- [İletişim Kutusu Denetimleri ve Bileşenleri](dialog-box-controls-and-components-windows-forms.md)
