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
ms.openlocfilehash: cd7b06030e0fb2bba74590ee80c07c34047c5b47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950618"
---
# <a name="how-to-invoke-a-print-dialog"></a>Nasıl yapılır: Yazdır İletişim Kutusu Çağırma
Uygulamadan yazdırabilme olanağı sağlamak için, bir <xref:System.Windows.Controls.PrintDialog> nesnesi oluşturup açmanız yeterlidir.  
  
## <a name="example"></a>Örnek  
 Denetim, yapılandırma ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] iş gönderimi için tek bir giriş noktası sağlar. <xref:System.Windows.Controls.PrintDialog> Denetim kullanımı kolaydır ve biçimlendirme veya kod kullanılarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oluşturulabilir. Aşağıdaki örnek, kodun kodda nasıl örneklendirileceğini ve bu denetimin nasıl yazdırılacağını gösterir. Ayrıca, iletişim kutusunun kullanıcıya belirli bir sayfa aralığını ayarlama seçeneğini sunmayacak şekilde nasıl emin olacağını gösterir. Örnek kod, C: sürücüsünün kökünde bir FixedDocumentSequence. XPS dosyası olduğunu varsayar.  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 İletişim kutusu açıldıktan sonra kullanıcılar, bilgisayarlarında yüklü olan yazıcıların arasından seçim yapabilir. Ayrıca, yazdırma yerine bir [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] dosya oluşturmak için [Microsoft XPS Belge Yazıcısı](https://go.microsoft.com/fwlink/?LinkId=147319) 'nı seçme seçeneği de vardır.  
  
> [!NOTE]
> Bu konu başlığı [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]altında açıklanan <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> denetim, Windows Forms bileşeniyle karıştırılmamalıdır. <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>  
  
 Kesinlikle konuşurken, iletişim kutusunu açmak zorunda <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> kalmadan yöntemini kullanabilirsiniz. Bu anlamda denetim, görülmeyen bir yazdırma bileşeni olarak kullanılabilir. Ancak performans <xref:System.Printing.PrintQueue.AddJob%2A> nedenleriyle, yöntemi veya ' nin <xref:System.Windows.Xps.XpsDocumentWriter>birçok <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yönteminden birini kullanmak daha iyi olacaktır. Bunun hakkında daha fazla bilgi için bkz. [Program aracılığıyla XPS dosyalarını ve yazdırma](how-to-programmatically-print-xps-files.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.PrintDialog>
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
- [Microsoft XPS Belge Yazıcısı](https://go.microsoft.com/fwlink/?LinkId=147319)
