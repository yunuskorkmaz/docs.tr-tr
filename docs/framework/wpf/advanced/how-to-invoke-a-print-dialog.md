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
ms.openlocfilehash: 75a4160366766efbd19d6e8ae26fbec102e7f95b
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924506"
---
# <a name="how-to-invoke-a-print-dialog"></a>Nasıl yapılır: Yazdır İletişim Kutusu Çağırma
Uygulamadan yazdırabilme olanağı sağlamak için, bir nesnesi oluşturup açmanız yeterlidir <xref:System.Windows.Controls.PrintDialog> .  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.PrintDialog>Denetim [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , yapılandırma ve XPS işi gönderimi için tek bir giriş noktası sağlar. Denetim kullanımı kolaydır ve [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] biçimlendirme veya kod kullanılarak oluşturulabilir. Aşağıdaki örnek, kodun kodda nasıl örneklendirileceğini ve bu denetimin nasıl yazdırılacağını gösterir. Ayrıca, iletişim kutusunun kullanıcıya belirli bir sayfa aralığını ayarlama seçeneğini sunmayacak şekilde nasıl emin olacağını gösterir. Örnek kod, C: sürücüsünün kökünde bir FixedDocumentSequence. XPS dosyası olduğunu varsayar.  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 İletişim kutusu açıldıktan sonra kullanıcılar, bilgisayarlarında yüklü olan yazıcıların arasından seçim yapabilir. Ayrıca, yazdırma yerine bir XML Kağıt Belirtimi (XPS) dosyası oluşturmak için [MICROSOFT XPS Belge Yazıcısı](/windows/win32/printdocs/microsoft-xps-document-writer) 'nı seçme seçeneği de vardır.  
  
> [!NOTE]
> <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>Bu konu başlığı altında AÇıKLANAN WPF denetimi, <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> Windows Forms bileşeniyle karıştırılmamalıdır.  
  
 Kesinlikle konuşurken, <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> iletişim kutusunu açmak zorunda kalmadan yöntemini kullanabilirsiniz. Bu anlamda denetim, görülmeyen bir yazdırma bileşeni olarak kullanılabilir. Ancak performans nedenleriyle, <xref:System.Printing.PrintQueue.AddJob%2A> yöntemi veya <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ' nin birçok ve yönteminden birini kullanmak daha iyi olacaktır <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> <xref:System.Windows.Xps.XpsDocumentWriter> . Bunun hakkında daha fazla bilgi için bkz. [Program aracılığıyla XPS dosyalarını yazdırma](how-to-programmatically-print-xps-files.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.PrintDialog>
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
- [Microsoft XPS Belge Yazıcısı](/windows/win32/printdocs/microsoft-xps-document-writer)
