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
ms.openlocfilehash: 2ced508eb83e2955fdcd1ad87fb6415e2052446f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206050"
---
# <a name="how-to-invoke-a-print-dialog"></a>Nasıl yapılır: Yazdır İletişim Kutusu Çağırma
Uygulamanızdan yazdırma olanağı sağlamak için basitçe oluşturabilir açın ve bir <xref:System.Windows.Controls.PrintDialog> nesne.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.PrintDialog> Denetim için tek giriş noktası sağlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], yapılandırması ve [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] iş gönderme. Kullanımı kolay bir denetimdir ve kullanarak oluşturulabilir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] biçimlendirmeyi veya kodu. Aşağıdaki örnek, örneği ve denetim code'da açın ve ondan yazdırmak nasıl gösterir. Ayrıca, iletişim kutusu sayfaları belirli bir aralığını ayarlama seçeneği kullanıcı sağlayacak emin olmak nasıl gösterir. Örnek kod, bir ' % s'dosyası FixedDocumentSequence.xps C: sürücüsünün kökündeki olduğunu varsayar.  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 İletişim kutusu açıldıktan sonra kullanıcıların bilgisayarlarında yüklü yazıcıları seçmek mümkün olacaktır. Bunlar ayrıca seçme seçeneğiniz olur. [Microsoft XPS Belge Yazıcısı](https://go.microsoft.com/fwlink/?LinkId=147319) oluşturmak için bir [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] yazdırma yerine dosya.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Denetimin [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bu konu başlığında ele alınmıştır karıştırılmamalıdır ile <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> Windows formlarının bileşen.  
  
 NET olarak söylemek gerekirse, kullanabileceğiniz <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> hiç iletişim kutusunu açmadan yöntemi. Bu anlamda denetimi görünmeyen bir yazdırma bileşeni olarak kullanılabilir. Ancak performansla ilgili nedenlerden dolayı ya da kullanılacak daha iyi olurdu <xref:System.Printing.PrintQueue.AddJob%2A> yöntemi veya çok biri <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemlerinin <xref:System.Windows.Xps.XpsDocumentWriter>. Bu konu hakkında daha fazla bilgi için bkz. [program aracılığıyla XPS dosyalarını yazdırma](how-to-programmatically-print-xps-files.md) ve.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.PrintDialog>
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
- [Microsoft XPS Belge Yazıcısı](https://go.microsoft.com/fwlink/?LinkId=147319)
