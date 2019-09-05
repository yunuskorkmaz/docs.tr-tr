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
ms.openlocfilehash: 4bad8158925fea8af529f70f92aad74e2a6bbec0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254108"
---
# <a name="how-to-invoke-a-print-dialog"></a>Nasıl yapılır: Yazdır İletişim Kutusu Çağırma
Uygulamadan yazdırabilme olanağı sağlamak için, bir <xref:System.Windows.Controls.PrintDialog> nesnesi oluşturup açmanız yeterlidir.  
  
## <a name="example"></a>Örnek  
 Denetim, yapılandırma ve XPS işi gönderimi için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]tek bir giriş noktası sağlar. <xref:System.Windows.Controls.PrintDialog> Denetim kullanımı kolaydır ve biçimlendirme veya kod kullanılarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oluşturulabilir. Aşağıdaki örnek, kodun kodda nasıl örneklendirileceğini ve bu denetimin nasıl yazdırılacağını gösterir. Ayrıca, iletişim kutusunun kullanıcıya belirli bir sayfa aralığını ayarlama seçeneğini sunmayacak şekilde nasıl emin olacağını gösterir. Örnek kod, C: sürücüsünün kökünde bir FixedDocumentSequence. XPS dosyası olduğunu varsayar.  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 İletişim kutusu açıldıktan sonra kullanıcılar, bilgisayarlarında yüklü olan yazıcıların arasından seçim yapabilir. Ayrıca, yazdırma yerine bir XML Kağıt Belirtimi (XPS) dosyası oluşturmak için [MICROSOFT XPS Belge Yazıcısı](https://go.microsoft.com/fwlink/?LinkId=147319) 'nı seçme seçeneği de vardır.  
  
> [!NOTE]
> Bu konu başlığı [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]altında açıklanan <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> denetim, Windows Forms bileşeniyle karıştırılmamalıdır. <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>  
  
 Kesinlikle konuşurken, iletişim kutusunu açmak zorunda <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> kalmadan yöntemini kullanabilirsiniz. Bu anlamda denetim, görülmeyen bir yazdırma bileşeni olarak kullanılabilir. Ancak performans <xref:System.Printing.PrintQueue.AddJob%2A> nedenleriyle, yöntemi veya ' nin <xref:System.Windows.Xps.XpsDocumentWriter>birçok <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yönteminden birini kullanmak daha iyi olacaktır. Bunun hakkında daha fazla bilgi için bkz. [Program aracılığıyla XPS dosyalarını ve yazdırma](how-to-programmatically-print-xps-files.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.PrintDialog>
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
- [Microsoft XPS Belge Yazıcısı](https://go.microsoft.com/fwlink/?LinkId=147319)
