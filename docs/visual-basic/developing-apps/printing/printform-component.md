---
title: PrintForm Bileşeni (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- PrintForm component [Visual Basic]
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
ms.openlocfilehash: 879d31c5a572689d84af6b2e46f3d33e1a8841c8
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649152"
---
# <a name="printform-component-visual-basic"></a>PrintForm Bileşeni (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Visual Basic için bileşen çalışma zamanında bir Windows Form görüntüsü yazdırmanızı sağlar. Bu davranışı yerini `PrintForm` Visual Basic'in önceki sürümlerindeki yöntemi.  
  
 PowerPack denetimleri artık Visual Studio'ya dahil, ancak bunları indirebilirsiniz [İndirme Merkezi](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="printform-component-overview"></a>PrintForm bileşeni genel bakış  
 Windows Forms için yaygın bir senaryo kağıt form veya bir raporu benzeyecek şekilde biçimlendirilmiş bir form oluşturmaktır ve ardından form görüntüsü yazdırmak için. Kullanabilirsiniz, ancak bir <xref:System.Drawing.Printing.PrintDocument> bileşen Bunu yapmak için bir sürü kod gerekir. <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen kullanmadan bir forma bir yazıcıya yazdırma önizleme penceresini veya bir dosya görüntüsü yazdırmanızı sağlar bir <xref:System.Drawing.Printing.PrintDocument> bileşeni.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşeni bulunur **Visual Basic PowerPacks** sekmesinde **araç kutusu**. Bir forma sürüklediğinizde küçük alanında form alt kenarlık bileşen tepsisinde görünür. Bileşeni seçildiğinde davranışını tanımlayan özellikleri ayarlanabilir **özellikleri** penceresi. Bu özelliklerin tümü, kod da ayarlanabilir. Ayrıca bir örneğini oluşturabilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> tasarım zamanında bileşeni eklemeden kodda bileşen.  
  
 Form yazdırma, formun istemci alanında her şey yazdırılmaz. Bu, tüm denetimler ve herhangi bir metin veya formda grafik yöntemleri tarafından çizilen grafik içerir. Varsayılan olarak, formun başlık çubuğu, kaydırma çubukları ve kenarlık yazdırılmaz. Ayrıca varsayılan <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşen yalnızca görünür bölüme formun yazdırır. Örneğin, kullanıcı çalışma zamanında bir formun boyutlandırırsa, yalnızca denetimleri ve şu anda görünür olan grafikleri yazdırılır.  
  
 Tarafından kullanılan varsayılan yazıcı <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşeni, işletim sisteminin Denetim Masası ayarları tarafından belirlenir.  
  
 Yazdırma başlatıldıktan sonra bir standart <xref:System.Drawing.Printing.PrintDocument> yazdırma iletişim kutusu görüntülenir. Bu iletişim kutusu, yazdırma işi iptal etmek kullanıcıların sağlar.  
  
### <a name="key-methods-properties-and-events"></a>Anahtar yöntemler, özellikler ve olaylar  
 Anahtar yöntemi <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşeni <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> yöntemi görüntüyü biçiminde bir yazıcı, yazdırma önizleme penceresini veya dosyaya yazdırır. İki sürümü vardır <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> yöntemi:  
  
-   Parametresiz bir temel sürüm: `Print()`  
  
-   Aşırı yüklenmiş bir sürümünü parametrelerle yazdırma davranışını belirtin: `Print(printForm As Form, printFormOption As PrintOption)`  
  
     `PrintOption` Aşırı yüklenmiş yöntemin parametre, form, formun başlık çubuğu, kaydırma çubukları ve kenarlık olup yazdırılır ve kaydırılabilir form bölümlerini olup yazdırılır yazdırmak için kullanılan temel uygulamayı belirler.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> Özelliktir anahtar özelliğine <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşeni. Bu özellik, çıkış bir yazıcıya gönderilir, baskı önizlemeyi penceresinde görüntülenen veya bir kapsüllenmiş PostScript'i dosyası olarak kaydedilen olup olmadığını belirler. Varsa <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> özelliği <xref:System.Drawing.Printing.PrintAction.PrintToFile>, <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> özellik yolu ve dosya adını belirtir.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> Özelliği için bir temel erişim sağlar <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A> yazıcı ve yazdırma kopya sayısı gibi ayarları belirtmenize olanak tanıyan bir nesne. Ayrıca, renk veya çift yönlü destek gibi yazıcının özellikler sorgulayabilirsiniz. Bu özellik görüntülenmez **özellikleri** penceresi; yalnızca koddan erişilebilir.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> Özellik çağırdığınızda yazdırmak için form belirtmek için kullanılır <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşen programlı olarak. Bileşen tasarım zamanında bir forma eklenirse, bu formu varsayılandır.  
  
 Anahtar olayları <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşen aşağıdakileri içerir:  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> olay. Gerçekleşir, <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> yöntemi çağrılır ve belge baskı siparişi'nın ilk sayfasında önce.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> olay. Son sayfa yazdırıldığında sonra gerçekleşir.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> olay. Her sayfa yazdırıldığında hemen önce gerçekleşir.  
  
### <a name="remarks"></a>Açıklamalar  
 Bir forma metin içeriyorsa veya grafikleri tarafından çizilen <xref:System.Drawing.Graphics> yöntemlerini kullanan temel <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> (`Print()`) yazdırmak için yöntemi. Grafikler bazı işletim sistemlerinde işlenemeyebilir, aşırı yüklenmiş <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> yöntemi kullanılır.  
  
 Bir formun genişliğine kağıdın yazıcının genişliğini daha geniş ise, formun sağ tarafında kesilebilir. Yazdırma için form tasarlarken, formun standart boyutlu kağıda sığdığından emin olun.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ortak kullanımını gösterir. <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> bileşeni.  
  
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
