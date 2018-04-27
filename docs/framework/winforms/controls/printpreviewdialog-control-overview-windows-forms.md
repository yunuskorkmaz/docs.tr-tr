---
title: PrintPreviewDialog Denetimine Genel Bakış (Windows Forms)
ms.custom: ''
ms.date: 01/08/2018
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5e5602a8aa4c83eb8dad33dff31f2dc0e7e7858e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>PrintPreviewDialog denetimine genel bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> denetimidir görüntülemek için kullanılan bir önceden yapılandırılmış iletişim kutusu nasıl bir [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) yazdırıldığında görünür. Kendi iletişim kutusu yapılandırma yerine basit bir çözüm olarak, Windows tabanlı uygulamanızda kullanın. Denetim yazdırma ve yakınlaştırma, bir veya birden çok sayfa görüntüleme ve iletişim kutusunu kapatmak için düğmeler içerir.  
  
## <a name="key-properties-and-methods"></a>Anahtar özellikleri ve yöntemleri  
 Denetimin anahtar özelliği <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, önizlemesi belgeye ayarlar. Belge olmalıdır bir <xref:System.Drawing.Printing.PrintDocument> nesnesi. İletişim kutusunu görüntülemek için çağırmalısınız kendi <xref:System.Windows.Forms.Form.ShowDialog%2A> yöntemi. Yumuşatma metnin sorunsuz görünmesini sağlayabilirsiniz, ancak daha yavaş görüntü yapabilirsiniz; Bunu kullanmak üzere ayarlanmış <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> özelliğine `true`.  
  
 Belirli özellikleri aracılığıyla kullanılabilir <xref:System.Windows.Forms.PrintPreviewControl> , <xref:System.Windows.Forms.PrintPreviewDialog> içerir. (Bu eklemek zorunda değilsiniz <xref:System.Windows.Forms.PrintPreviewControl> forma; bu otomatik olarak içinde yer <xref:System.Windows.Forms.PrintPreviewDialog> formunuza iletişim eklediğinizde.) Aracılığıyla kullanılabilen özellikleri örnekleri <xref:System.Windows.Forms.PrintPreviewControl> olan <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> ve <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> yatay ve dikey olarak denetiminde görüntülenen sayfaların sayısını belirlemek özellikleri. Erişebileceğiniz <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> özelliği olarak `PrintPreviewDialog1.PrintPreviewControl.Columns` Visual Basic'te `printPreviewDialog1.PrintPreviewControl.Columns` Visual C# ' ta, veya `printPreviewDialog1->PrintPreviewControl->Columns` içinde [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].  
  
## <a name="printpreviewdialog-performance"></a>PrintPreviewDialog performans

Aşağıdaki koşullarda <xref:System.Windows.Forms.PrintPreviewDialog> denetim başlatan çok yavaş:

- Ağ yazıcısı kullanılır.
- Çift yönlü ayarları gibi bu yazıcıyı ilgili kullanıcı tercihlerini değiştirilir.
  
.NET Framework 4.5.2 çalışan uygulamalar için aşağıdaki anahtara ekleyebilirsiniz \<appSettings > performansını artırmak için yapılandırma dosyasının <xref:System.Windows.Forms.PrintPreviewDialog> başlatma denetleme:

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
Varsa `EnablePrintPreviewOptimization` ayarlayan başka bir değer veya anahtar mevcut değilse, en iyi duruma getirme uygulanmaz.

.NET Framework 4.6 veya sonraki sürümlerde çalışan uygulamalar için aşağıdaki anahtara ekleyebilirsiniz [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ \<çalışma zamanı >](../../configure-apps/file-schema/runtime/index.md) Uygulama yapılandırma dosyası bölümünü:

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
Anahtar mevcut değilse veya başka bir değer ayarlarsanız, en iyi duruma getirme uygulanmıyor. 

Kullanırsanız <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> performansını yazıcı ayarlarını değiştirmek için olay <xref:System.Windows.Forms.PrintPreviewDialog> denetimi değil artırmaya bir en iyi duruma getirme yapılandırma anahtarı ayarlasanız bile.  

## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [PrintPreviewControl Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [PrintPreviewDialog Denetimi](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [İletişim Kutusu Denetimleri ve Bileşenleri](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
