---
title: 'Nasıl yapılır: Yazdır İletişim Kutusu Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 6d7bc322079718d17a921ef34af79145b021e3a7
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636100"
---
# <a name="how-to-invoke-a-print-dialog"></a>Nasıl yapılır: Yazdır İletişim Kutusu Çağırma
Uygulamadan yazdırabilme olanağı sağlamak için bir <xref:System.Windows.Controls.PrintDialog> nesnesi oluşturup açabilirsiniz.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.PrintDialog> denetimi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], yapılandırma ve XPS işi gönderimi için tek bir giriş noktası sağlar. Denetim kullanımı kolaydır ve [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] biçimlendirme veya kod kullanılarak oluşturulabilir. Aşağıdaki örnek, kodun kodda nasıl örneklendirileceğini ve bu denetimin nasıl yazdırılacağını gösterir. Ayrıca, iletişim kutusunun kullanıcıya belirli bir sayfa aralığını ayarlama seçeneğini sunmayacak şekilde nasıl emin olacağını gösterir. Örnek kod, C: sürücüsünün kökünde bir FixedDocumentSequence. XPS dosyası olduğunu varsayar.  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 İletişim kutusu açıldıktan sonra kullanıcılar, bilgisayarlarında yüklü olan yazıcıların arasından seçim yapabilir. Ayrıca, yazdırma yerine bir XML Kağıt Belirtimi (XPS) dosyası oluşturmak için [MICROSOFT XPS Belge Yazıcısı](https://go.microsoft.com/fwlink/?LinkId=147319) 'nı seçme seçeneği de vardır.  
  
> [!NOTE]
> Bu konuda açıklanan WPF <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> denetimi, Windows Forms <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> bileşeniyle karıştırılmamalıdır.  
  
 Kesinlikle konuşurken, iletişim kutusunu açmadan <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> yöntemini kullanabilirsiniz. Bu anlamda denetim, görülmeyen bir yazdırma bileşeni olarak kullanılabilir. Ancak, performans nedenleriyle <xref:System.Printing.PrintQueue.AddJob%2A> yöntemi veya <xref:System.Windows.Xps.XpsDocumentWriter><xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemlerinden birini kullanmak daha iyi olacaktır. Bunun hakkında daha fazla bilgi için bkz. [Program aracılığıyla XPS dosyalarını ve yazdırma](how-to-programmatically-print-xps-files.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.PrintDialog>
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
- [Microsoft XPS Belge Yazıcısı](https://go.microsoft.com/fwlink/?LinkId=147319)
