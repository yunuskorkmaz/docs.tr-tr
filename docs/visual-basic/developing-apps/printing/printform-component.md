---
title: PrintForm Bileşeni (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- PrintForm component [Visual Basic]
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 890d5a3a3f9c3a737a59e17fef0d4ac0407e9924
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/10/2018
---
# <a name="printform-component-visual-basic"></a>PrintForm Bileşeni (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> İçin bileşen [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] çalışma zamanında bir Windows formunda bir görüntüsünü yazdırmanızı sağlar. ' Nın davranışını değiştirir `PrintForm` Visual Basic önceki sürümlerinde yöntemi.  
  
 PowerPack denetimleri artık Visual Studio'ya dahil olan, ancak bunları indirebilirsiniz [Yükleme Merkezi'nden](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="printform-component-overview"></a>PrintForm bileşeni genel bakış  
 Windows Forms için yaygın bir senaryo kağıt form veya bir rapor benzeyecek şekilde biçimlendirilmiş bir form oluşturmaktır ve ardından form görüntüsü yazdırmak için. Kullanabilirsiniz ancak bir <xref:System.Drawing.Printing.PrintDocument> Bunu yapmak için bileşeni çok fazla kod gerekir. <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen kullanmadan bir yazıcı, Baskı Önizleme penceresinden veya bir dosyayı bir form görüntüsü yazdırma olanak tanır bir <xref:System.Drawing.Printing.PrintDocument> bileşeni.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen bulunur **Visual Basic PowerPacks** sekmesinde **araç**. Bir forma sürüklendiğinde bileşen alanındaki küçük alanı alt kenarlık formunun altında görünür. Bileşen seçildiğinde davranışını tanımlayan özellikleri ayarlanabilir **özellikleri** penceresi. Bu özelliklerin tümü, kodda de ayarlanabilir. Ayrıca bir örneğini oluşturabilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> tasarım zamanında bileşen eklemeden kodda bileşen.  
  
 Bir formu yazdırırken, her şeyi formun istemci alanını yazdırılır. Bu, tüm denetimler ve herhangi bir metin veya formda grafik yöntemler tarafından çizilmiş grafik içerir. Varsayılan olarak, formun başlık çubuğu, kaydırma çubukları ve kenarlık yazdırılır değil. Ayrıca varsayılan <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşen form yalnızca görünür kısmını yazdırır. Örneğin, kullanıcı çalışma zamanında formun boyutlandırırsa, yalnızca denetimleri ve görüntülenmekte olan grafik yazdırılır.  
  
 Tarafından kullanılan varsayılan yazıcı <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşeni işletim sisteminin Denetim Masası ayarları tarafından belirlenir.  
  
 Yazdırma başlatıldıktan sonra standart bir <xref:System.Drawing.Printing.PrintDocument> yazdırma iletişim kutusu görüntülenir. Bu iletişim kutusu, yazdırma işi iptal etmek kullanıcıların sağlar.  
  
### <a name="key-methods-properties-and-events"></a>Anahtar yöntemler, özellikler ve olaylar  
 Anahtar yöntemi <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşeni <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> yazıcı, Baskı Önizleme penceresinden veya dosya biçimine görüntüsünü yazdırır yöntemi. İki sürümü vardır <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> yöntemi:  
  
-   Parametresiz bir temel sürüm: `Print()`  
  
-   Aşırı yüklenmiş bir sürümünü parametrelerle yazdırma davranışını belirtin: `Print(printForm As Form, printFormOption As PrintOption)`  
  
     `PrintOption` Aşırı yüklenmiş yöntemin parametre form, formun başlık çubuğu, kaydırma çubukları ve kenarlık olup yazdırılır ve formun kaydırılabilir bölümleri olup yazdırılır yazdırmak için kullanılan temel uygulaması belirler.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> Özelliktir anahtar özelliğine <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşeni. Bu özellik, çıkış bir yazıcıya gönderildi, Baskı Önizleme penceresinde görüntülenen veya PostScript'i kapsüllenmiş dosyası olarak kaydedilen olup olmadığını belirler. Varsa <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> özelliği ayarlanmış <xref:System.Drawing.Printing.PrintAction.PrintToFile>, <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> özelliği yol ve dosya adını belirtir.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> Özelliği sağlar bir arka plandaki erişimi <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A> yazıcı ve kopya sayısı olarak gibi ayarlarını belirtmenize olanak tanıyan nesnesi. Renk veya çift yönlü destek gibi yazıcının özelliklerine de sorgulayabilirsiniz. Bu özellik görünmez **özellikleri** penceresi; yalnızca koddan erişilebilir.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> Özelliği çağırdığınızda, yazdırma forma belirtmek için kullanılır <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşen programlı olarak. Bileşen bir forma tasarım zamanında eklediyseniz, bu formda varsayılandır.  
  
 Anahtar için olayları <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşen aşağıdakileri içerir:  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> olay. Oluşur, <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> yöntemi çağrılır ve belge baskı siparişi'nın ilk sayfasında önce.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> olay. Son sayfayı yazdırılan sonra gerçekleşir.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> olay. Her bir sayfa hemen yazdırılır önce gerçekleşir.  
  
### <a name="remarks"></a>Açıklamalar  
 Bir form metin içeriyorsa veya tarafından çizilmiş grafik <xref:System.Drawing.Graphics> yöntemlerini kullanın temel <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> (`Print()`) yazdırmak için yöntem. Grafik bazı işletim sistemlerinde değil işlemek, aşırı yüklenmiş <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> yöntemi kullanılır.  
  
 Bir form genişliğini yazıcıya kağıt genişliğini daha geniş ise, formun sağ tarafındaki kesilmiş. Yazdırma için form tasarlarken, formun standart boyutlu kağıda uygun emin olun.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, genel kullanımı, gösterir <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşeni.  
  
```  
' Visual Basic.  
Dim pf As New PrintForm  
pf.Form = Me  
pf.PrintAction = PrintToPrinter  
pf.Print()  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 [Nasıl Yapılır: PrintForm Bileşenini Kullanarak Form Yazdırma](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md)  
 [Nasıl Yapılır: Formun İstemci Alanını Yazdırma](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [Nasıl Yapılır: Formun İstemci Alanlarını ve Diğerlerini Yazdırma](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [Nasıl Yapılır: Kaydırılabilir Form Yazdırma](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
