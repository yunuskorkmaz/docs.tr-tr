---
title: PrintPreviewDialog Denetimine Genel Bakış (Windows Forms)
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 961b3c852f60a0917707bef07d4e26fc4215acca
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611126"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>PrintPreviewDialog denetimine genel bakış (Windows Forms)

Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> denetimidir görüntülemek için kullanılan bir önceden yapılandırılmış bir iletişim kutusu nasıl bir [PrintDocument](printdocument-component-windows-forms.md) yazdırıldığında görünür. Windows tabanlı uygulamanızda kendi iletişim kutusu yapılandırmak yerine basit bir çözüm olarak kullanın. Yazdırma ve yakınlaştırma, bir veya birden çok sayfa görüntüleme ve iletişim kutusunu kapatmak için düğme denetimi içerir.

## <a name="key-properties-and-methods"></a>Anahtar özellikleri ve yöntemleri

Denetimin anahtar özelliği <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, belgenin önizlemesi için ayarlar. Belge olmalıdır bir <xref:System.Drawing.Printing.PrintDocument> nesne. İletişim kutusunu görüntülemek için çağırmalıdır kendi <xref:System.Windows.Forms.Form.ShowDialog%2A> yöntemi. Daha sorunsuz yükseltmelere görünen metin düzgünleştirme yapabilirsiniz, ancak daha yavaş görünen yapabilirsiniz; Bunu kullanmak için ayarlanmış <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> özelliğini `true`.

Bazı özellikler aracılığıyla kullanılabilir <xref:System.Windows.Forms.PrintPreviewControl> , <xref:System.Windows.Forms.PrintPreviewDialog> içerir. (Bunu eklemek zorunda değilsiniz <xref:System.Windows.Forms.PrintPreviewControl> forma; bunu otomatik olarak içerdiği <xref:System.Windows.Forms.PrintPreviewDialog> formunuza iletişim kutusu eklediğinizde,.) Aracılığıyla kullanılabilen özellikleri örnekleri <xref:System.Windows.Forms.PrintPreviewControl> olan <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> ve <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> denetimde yatay ve dikey olarak görüntülenen sayfa sayısını belirleyen özellikleri. Erişebildiğiniz <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> özelliği olarak `PrintPreviewDialog1.PrintPreviewControl.Columns` Visual Basic'te `printPreviewDialog1.PrintPreviewControl.Columns` görselde C#, veya `printPreviewDialog1->PrintPreviewControl->Columns` içinde [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].

## <a name="printpreviewdialog-performance"></a>PrintPreviewDialog performans

Aşağıdaki koşullarda <xref:System.Windows.Forms.PrintPreviewDialog> denetimi çok yavaş başlatır:

- Ağ yazıcısı kullanılır.
- Çift yönlü ayarları gibi bu yazıcı için kullanıcı tercihlerini değiştirilir.

.NET Framework 4.5.2 üzerinde çalışan uygulamalar için aşağıdaki anahtara ekleyebilirsiniz \<appSettings > performansını artırmak için yapılandırma dosyasının <xref:System.Windows.Forms.PrintPreviewDialog> başlatma denetimi:

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

Varsa `EnablePrintPreviewOptimization` ayarlayan başka bir değer veya anahtar mevcut değilse, en iyi duruma getirme uygulanmaz.

.NET Framework 4.6 veya sonraki sürümler üzerinde çalışan uygulamalar için aşağıdaki anahtara ekleyebilirsiniz [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ \<çalışma zamanı >](../../configure-apps/file-schema/runtime/index.md) Uygulama yapılandırma dosyanızı bölümü:

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

Anahtar mevcut değilse veya diğer herhangi bir değere ayarlarsanız, iyileştirme uygulanmaz.

Kullanırsanız <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> performansını yazıcı ayarlarını değiştirmek için olay <xref:System.Windows.Forms.PrintPreviewDialog> denetimi değil artıracak bir iyileştirme yapılandırma anahtarı olarak ayarlanmış olsa bile.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [PrintPreviewControl Denetimine Genel Bakış](printpreviewcontrol-control-overview-windows-forms.md)
- [PrintPreviewDialog Denetimi](printpreviewdialog-control-windows-forms.md)
- [İletişim Kutusu Denetimleri ve Bileşenleri](dialog-box-controls-and-components-windows-forms.md)
