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
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="3639a-102">Printönizleme Iletişim kutusu denetimine genel bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="3639a-102">PrintPreviewDialog control overview (Windows Forms)</span></span>

<span data-ttu-id="3639a-103">Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> denetimi, yazdırıldığında bir [PrintDocument](printdocument-component-windows-forms.md) 'ın nasıl görüneceğini göstermek için kullanılan önceden yapılandırılmış bir iletişim kutusudur.</span><span class="sxs-lookup"><span data-stu-id="3639a-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="3639a-104">Kendi iletişim kutusunu yapılandırmak yerine, bunu Windows tabanlı uygulamanızda basit bir çözüm olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="3639a-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="3639a-105">Denetim, yazdırma, yakınlaştırma, bir veya birden çok sayfa görüntüleme ve iletişim kutusunu kapatma düğmelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3639a-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="3639a-106">Anahtar özellikleri ve yöntemleri</span><span class="sxs-lookup"><span data-stu-id="3639a-106">Key properties and methods</span></span>

<span data-ttu-id="3639a-107">Denetimin anahtar özelliği, belgeyi önizlenen olarak ayarlayan <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>.</span><span class="sxs-lookup"><span data-stu-id="3639a-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="3639a-108">Belge bir <xref:System.Drawing.Printing.PrintDocument> nesnesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3639a-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="3639a-109">İletişim kutusunu göstermek için <xref:System.Windows.Forms.Form.ShowDialog%2A> yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3639a-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="3639a-110">Kenar yumuşatma, metnin daha düzgün görünmesine neden olabilir, ancak aynı zamanda ekranı daha yavaş hale getirir; kullanmak için <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3639a-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>

<span data-ttu-id="3639a-111">Bazı özellikler <xref:System.Windows.Forms.PrintPreviewDialog> içeren <xref:System.Windows.Forms.PrintPreviewControl> ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3639a-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="3639a-112">(Bu <xref:System.Windows.Forms.PrintPreviewControl> forma eklemeniz gerekmez; iletişim kutusunu formunuza eklediğinizde otomatik olarak <xref:System.Windows.Forms.PrintPreviewDialog> içinde yer alır.) <xref:System.Windows.Forms.PrintPreviewControl> aracılığıyla kullanılabilen özelliklerin örnekleri, denetimde yatay ve dikey olarak görüntülenen sayfa sayısını belirleyen <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> ve <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="3639a-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="3639a-113"><xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> özelliğine Visual Basic, görselde C#`printPreviewDialog1.PrintPreviewControl.Columns` veya görselde C++`printPreviewDialog1->PrintPreviewControl->Columns` `PrintPreviewDialog1.PrintPreviewControl.Columns` olarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3639a-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` in Visual C#, or `printPreviewDialog1->PrintPreviewControl->Columns` in Visual C++.</span></span>

## <a name="printpreviewdialog-performance"></a><span data-ttu-id="3639a-114">Printönizleme Iletişim kutusu performansı</span><span class="sxs-lookup"><span data-stu-id="3639a-114">PrintPreviewDialog performance</span></span>

<span data-ttu-id="3639a-115">Aşağıdaki koşullarda <xref:System.Windows.Forms.PrintPreviewDialog> denetimi çok yavaş başlatılır:</span><span class="sxs-lookup"><span data-stu-id="3639a-115">Under the following conditions, the <xref:System.Windows.Forms.PrintPreviewDialog> control initializes very slowly:</span></span>

- <span data-ttu-id="3639a-116">Bir ağ yazıcısı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3639a-116">A network printer is used.</span></span>
- <span data-ttu-id="3639a-117">Bu yazıcı için çift yönlü ayarlar gibi Kullanıcı tercihleri değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="3639a-117">User preferences for this printer, such as duplex settings, are modified.</span></span>

<span data-ttu-id="3639a-118">.NET Framework 4.5.2 üzerinde çalışan uygulamalar için, <xref:System.Windows.Forms.PrintPreviewDialog> denetimi başlatma performansını geliştirmek için yapılandırma dosyanızın \<appSettings > bölümüne aşağıdaki anahtarı ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3639a-118">For apps running on the .NET Framework 4.5.2, you can add the following key to the \<appSettings> section of your configuration file to improve the performance of <xref:System.Windows.Forms.PrintPreviewDialog> control initialization:</span></span>

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

<span data-ttu-id="3639a-119">`EnablePrintPreviewOptimization` anahtarı başka bir değere ayarlandıysa veya anahtar yoksa, iyileştirme uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="3639a-119">If the `EnablePrintPreviewOptimization` key is set to any other value, or if the key is not present, the optimization is not applied.</span></span>

<span data-ttu-id="3639a-120">.NET Framework 4,6 veya sonraki sürümlerde çalışan uygulamalar için, uygulama yapılandırma dosyanızın [\<runtime >](../../configure-apps/file-schema/runtime/index.md) bölümünde yer alan [\<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesine aşağıdaki anahtarı ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3639a-120">For apps running on the .NET Framework 4.6 or later versions, you can add the following switch to the [\<AppContextSwitchOverrides>](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [\<runtime>](../../configure-apps/file-schema/runtime/index.md) section of your app config file:</span></span>

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

<span data-ttu-id="3639a-121">Anahtar yoksa veya başka bir değere ayarlandıysa, iyileştirme uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="3639a-121">If the switch is not present or if it is set to any other value, the optimization is not applied.</span></span>

<span data-ttu-id="3639a-122">Yazıcı ayarlarını değiştirmek için <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> olayını kullanırsanız, bir iyileştirme yapılandırma anahtarı ayarlanmış olsa bile <xref:System.Windows.Forms.PrintPreviewDialog> denetiminin performansı geliştirilecektir.</span><span class="sxs-lookup"><span data-stu-id="3639a-122">If you use the <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> event to modify printer settings, the performance of the <xref:System.Windows.Forms.PrintPreviewDialog> control will not improve even if an optimization configuration switch is set.</span></span>

## <a name="see-also"></a><span data-ttu-id="3639a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3639a-123">See also</span></span>

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [<span data-ttu-id="3639a-124">PrintPreviewControl Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3639a-124">PrintPreviewControl Control Overview</span></span>](printpreviewcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="3639a-125">PrintPreviewDialog Denetimi</span><span class="sxs-lookup"><span data-stu-id="3639a-125">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="3639a-126">İletişim Kutusu Denetimleri ve Bileşenleri</span><span class="sxs-lookup"><span data-stu-id="3639a-126">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
