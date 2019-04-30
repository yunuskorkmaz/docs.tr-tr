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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757164"
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="deab8-102">Nasıl yapılır: Yazdır İletişim Kutusu Çağırma</span><span class="sxs-lookup"><span data-stu-id="deab8-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="deab8-103">Uygulamanızdan yazdırma olanağı sağlamak için basitçe oluşturabilir açın ve bir <xref:System.Windows.Controls.PrintDialog> nesne.</span><span class="sxs-lookup"><span data-stu-id="deab8-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="deab8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="deab8-104">Example</span></span>  
 <span data-ttu-id="deab8-105"><xref:System.Windows.Controls.PrintDialog> Denetim için tek giriş noktası sağlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], yapılandırması ve [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] iş gönderme.</span><span class="sxs-lookup"><span data-stu-id="deab8-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] job submission.</span></span> <span data-ttu-id="deab8-106">Kullanımı kolay bir denetimdir ve kullanarak oluşturulabilir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] biçimlendirmeyi veya kodu.</span><span class="sxs-lookup"><span data-stu-id="deab8-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="deab8-107">Aşağıdaki örnek, örneği ve denetim code'da açın ve ondan yazdırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="deab8-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="deab8-108">Ayrıca, iletişim kutusu sayfaları belirli bir aralığını ayarlama seçeneği kullanıcı sağlayacak emin olmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="deab8-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="deab8-109">Örnek kod, bir ' % s'dosyası FixedDocumentSequence.xps C: sürücüsünün kökündeki olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="deab8-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="deab8-110">İletişim kutusu açıldıktan sonra kullanıcıların bilgisayarlarında yüklü yazıcıları seçmek mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="deab8-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="deab8-111">Bunlar ayrıca seçme seçeneğiniz olur. [Microsoft XPS Belge Yazıcısı](https://go.microsoft.com/fwlink/?LinkId=147319) oluşturmak için bir [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] yazdırma yerine dosya.</span><span class="sxs-lookup"><span data-stu-id="deab8-111">They will also have the option of selecting the [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319) to create an [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] file instead of printing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="deab8-112"><xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Denetimin [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bu konu başlığında ele alınmıştır karıştırılmamalıdır ile <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> Windows formlarının bileşen.</span><span class="sxs-lookup"><span data-stu-id="deab8-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of Windows Forms.</span></span>  
  
 <span data-ttu-id="deab8-113">NET olarak söylemek gerekirse, kullanabileceğiniz <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> hiç iletişim kutusunu açmadan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="deab8-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="deab8-114">Bu anlamda denetimi görünmeyen bir yazdırma bileşeni olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="deab8-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="deab8-115">Ancak performansla ilgili nedenlerden dolayı ya da kullanılacak daha iyi olurdu <xref:System.Printing.PrintQueue.AddJob%2A> yöntemi veya çok biri <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemlerinin <xref:System.Windows.Xps.XpsDocumentWriter>.</span><span class="sxs-lookup"><span data-stu-id="deab8-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="deab8-116">Bu konu hakkında daha fazla bilgi için bkz. [program aracılığıyla XPS dosyalarını yazdırma](how-to-programmatically-print-xps-files.md) ve.</span><span class="sxs-lookup"><span data-stu-id="deab8-116">For more about this, see [Programmatically Print XPS Files](how-to-programmatically-print-xps-files.md) and .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deab8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="deab8-117">See also</span></span>

- <xref:System.Windows.Controls.PrintDialog>
- [<span data-ttu-id="deab8-118">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="deab8-118">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="deab8-119">Yazdırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="deab8-119">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="deab8-120">Microsoft XPS Belge Yazıcısı</span><span class="sxs-lookup"><span data-stu-id="deab8-120">Microsoft XPS Document Writer</span></span>](https://go.microsoft.com/fwlink/?LinkId=147319)
