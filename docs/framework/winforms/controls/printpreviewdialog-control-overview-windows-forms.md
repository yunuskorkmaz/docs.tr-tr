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
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="0c758-102">PrintPreviewDialog denetimine genel bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0c758-102">PrintPreviewDialog control overview (Windows Forms)</span></span>
<span data-ttu-id="0c758-103">Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> denetimidir görüntülemek için kullanılan bir önceden yapılandırılmış iletişim kutusu nasıl bir [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) yazdırıldığında görünür.</span><span class="sxs-lookup"><span data-stu-id="0c758-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="0c758-104">Kendi iletişim kutusu yapılandırma yerine basit bir çözüm olarak, Windows tabanlı uygulamanızda kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c758-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="0c758-105">Denetim yazdırma ve yakınlaştırma, bir veya birden çok sayfa görüntüleme ve iletişim kutusunu kapatmak için düğmeler içerir.</span><span class="sxs-lookup"><span data-stu-id="0c758-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="0c758-106">Anahtar özellikleri ve yöntemleri</span><span class="sxs-lookup"><span data-stu-id="0c758-106">Key properties and methods</span></span>  
 <span data-ttu-id="0c758-107">Denetimin anahtar özelliği <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, önizlemesi belgeye ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0c758-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="0c758-108">Belge olmalıdır bir <xref:System.Drawing.Printing.PrintDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="0c758-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="0c758-109">İletişim kutusunu görüntülemek için çağırmalısınız kendi <xref:System.Windows.Forms.Form.ShowDialog%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0c758-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="0c758-110">Yumuşatma metnin sorunsuz görünmesini sağlayabilirsiniz, ancak daha yavaş görüntü yapabilirsiniz; Bunu kullanmak üzere ayarlanmış <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="0c758-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="0c758-111">Belirli özellikleri aracılığıyla kullanılabilir <xref:System.Windows.Forms.PrintPreviewControl> , <xref:System.Windows.Forms.PrintPreviewDialog> içerir.</span><span class="sxs-lookup"><span data-stu-id="0c758-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="0c758-112">(Bu eklemek zorunda değilsiniz <xref:System.Windows.Forms.PrintPreviewControl> forma; bu otomatik olarak içinde yer <xref:System.Windows.Forms.PrintPreviewDialog> formunuza iletişim eklediğinizde.) Aracılığıyla kullanılabilen özellikleri örnekleri <xref:System.Windows.Forms.PrintPreviewControl> olan <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> ve <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> yatay ve dikey olarak denetiminde görüntülenen sayfaların sayısını belirlemek özellikleri.</span><span class="sxs-lookup"><span data-stu-id="0c758-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="0c758-113">Erişebileceğiniz <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> özelliği olarak `PrintPreviewDialog1.PrintPreviewControl.Columns` Visual Basic'te `printPreviewDialog1.PrintPreviewControl.Columns` Visual C# ' ta, veya `printPreviewDialog1->PrintPreviewControl->Columns` içinde [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0c758-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` in Visual C#, or `printPreviewDialog1->PrintPreviewControl->Columns` in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].</span></span>  
  
## <a name="printpreviewdialog-performance"></a><span data-ttu-id="0c758-114">PrintPreviewDialog performans</span><span class="sxs-lookup"><span data-stu-id="0c758-114">PrintPreviewDialog performance</span></span>

<span data-ttu-id="0c758-115">Aşağıdaki koşullarda <xref:System.Windows.Forms.PrintPreviewDialog> denetim başlatan çok yavaş:</span><span class="sxs-lookup"><span data-stu-id="0c758-115">Under the following conditions, the <xref:System.Windows.Forms.PrintPreviewDialog> control initializes very slowly:</span></span>

- <span data-ttu-id="0c758-116">Ağ yazıcısı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0c758-116">A network printer is used.</span></span>
- <span data-ttu-id="0c758-117">Çift yönlü ayarları gibi bu yazıcıyı ilgili kullanıcı tercihlerini değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="0c758-117">User preferences for this printer, such as duplex settings, are modified.</span></span>
  
<span data-ttu-id="0c758-118">.NET Framework 4.5.2 çalışan uygulamalar için aşağıdaki anahtara ekleyebilirsiniz \<appSettings > performansını artırmak için yapılandırma dosyasının <xref:System.Windows.Forms.PrintPreviewDialog> başlatma denetleme:</span><span class="sxs-lookup"><span data-stu-id="0c758-118">For apps running on the .NET Framework 4.5.2, you can add the following key to the \<appSettings> section of your configuration file to improve the performance of <xref:System.Windows.Forms.PrintPreviewDialog> control initialization:</span></span>

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
<span data-ttu-id="0c758-119">Varsa `EnablePrintPreviewOptimization` ayarlayan başka bir değer veya anahtar mevcut değilse, en iyi duruma getirme uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="0c758-119">If the `EnablePrintPreviewOptimization` key is set to any other value, or if the key is not present, the optimization is not applied.</span></span>

<span data-ttu-id="0c758-120">.NET Framework 4.6 veya sonraki sürümlerde çalışan uygulamalar için aşağıdaki anahtara ekleyebilirsiniz [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ \<çalışma zamanı >](../../configure-apps/file-schema/runtime/index.md) Uygulama yapılandırma dosyası bölümünü:</span><span class="sxs-lookup"><span data-stu-id="0c758-120">For apps running on the .NET Framework 4.6 or later versions, you can add the following switch to the [\<AppContextSwitchOverrides>](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [\<runtime>](../../configure-apps/file-schema/runtime/index.md) section of your app config file:</span></span>

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
<span data-ttu-id="0c758-121">Anahtar mevcut değilse veya başka bir değer ayarlarsanız, en iyi duruma getirme uygulanmıyor.</span><span class="sxs-lookup"><span data-stu-id="0c758-121">If the switch is not present or if it is set to any other value, the optimization is not applied.</span></span> 

<span data-ttu-id="0c758-122">Kullanırsanız <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> performansını yazıcı ayarlarını değiştirmek için olay <xref:System.Windows.Forms.PrintPreviewDialog> denetimi değil artırmaya bir en iyi duruma getirme yapılandırma anahtarı ayarlasanız bile.</span><span class="sxs-lookup"><span data-stu-id="0c758-122">If you use the <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> event to modify printer settings, the performance of the <xref:System.Windows.Forms.PrintPreviewDialog> control will not improve even if an optimization configuration switch is set.</span></span>  

## <a name="see-also"></a><span data-ttu-id="0c758-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c758-123">See also</span></span>  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [<span data-ttu-id="0c758-124">PrintPreviewControl Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0c758-124">PrintPreviewControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="0c758-125">PrintPreviewDialog Denetimi</span><span class="sxs-lookup"><span data-stu-id="0c758-125">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="0c758-126">İletişim Kutusu Denetimleri ve Bileşenleri</span><span class="sxs-lookup"><span data-stu-id="0c758-126">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
