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
ms.openlocfilehash: f7ef3312d876324b44b055d70fd22e3fba075ec6
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095183"
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="d7bf9-102">Nasıl yapılır: Yazdır İletişim Kutusu Çağırma</span><span class="sxs-lookup"><span data-stu-id="d7bf9-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="d7bf9-103">Uygulamadan yazdırabilme olanağı sağlamak için bir <xref:System.Windows.Controls.PrintDialog> nesnesi oluşturup açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7bf9-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7bf9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7bf9-104">Example</span></span>  
 <span data-ttu-id="d7bf9-105"><xref:System.Windows.Controls.PrintDialog> denetimi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], yapılandırma ve XPS işi gönderimi için tek bir giriş noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7bf9-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and XPS job submission.</span></span> <span data-ttu-id="d7bf9-106">Denetim kullanımı kolaydır ve [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] biçimlendirme veya kod kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="d7bf9-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="d7bf9-107">Aşağıdaki örnek, kodun kodda nasıl örneklendirileceğini ve bu denetimin nasıl yazdırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7bf9-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="d7bf9-108">Ayrıca, iletişim kutusunun kullanıcıya belirli bir sayfa aralığını ayarlama seçeneğini sunmayacak şekilde nasıl emin olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7bf9-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="d7bf9-109">Örnek kod, C: sürücüsünün kökünde bir FixedDocumentSequence. XPS dosyası olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="d7bf9-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="d7bf9-110">İletişim kutusu açıldıktan sonra kullanıcılar, bilgisayarlarında yüklü olan yazıcıların arasından seçim yapabilir.</span><span class="sxs-lookup"><span data-stu-id="d7bf9-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="d7bf9-111">Ayrıca, yazdırma yerine bir XML Kağıt Belirtimi (XPS) dosyası oluşturmak için [MICROSOFT XPS Belge Yazıcısı](/windows/win32/printdocs/microsoft-xps-document-writer) 'nı seçme seçeneği de vardır.</span><span class="sxs-lookup"><span data-stu-id="d7bf9-111">They will also have the option of selecting the [Microsoft XPS Document Writer](/windows/win32/printdocs/microsoft-xps-document-writer) to create an XML Paper Specification (XPS) file instead of printing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7bf9-112">Bu konuda açıklanan WPF <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> denetimi, Windows Forms <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> bileşeniyle karıştırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7bf9-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of WPF, which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of Windows Forms.</span></span>  
  
 <span data-ttu-id="d7bf9-113">Kesinlikle konuşurken, iletişim kutusunu açmadan <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7bf9-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="d7bf9-114">Bu anlamda denetim, görülmeyen bir yazdırma bileşeni olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d7bf9-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="d7bf9-115">Ancak, performans nedenleriyle <xref:System.Printing.PrintQueue.AddJob%2A> yöntemi veya <xref:System.Windows.Xps.XpsDocumentWriter><xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemlerinden birini kullanmak daha iyi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d7bf9-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="d7bf9-116">Bunun hakkında daha fazla bilgi için bkz. [Program aracılığıyla XPS dosyalarını ve yazdırma](how-to-programmatically-print-xps-files.md) .</span><span class="sxs-lookup"><span data-stu-id="d7bf9-116">For more about this, see [Programmatically Print XPS Files](how-to-programmatically-print-xps-files.md) and .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7bf9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7bf9-117">See also</span></span>

- <xref:System.Windows.Controls.PrintDialog>
- [<span data-ttu-id="d7bf9-118">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="d7bf9-118">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="d7bf9-119">Yazdırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d7bf9-119">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="d7bf9-120">Microsoft XPS Belge Yazıcısı</span><span class="sxs-lookup"><span data-stu-id="d7bf9-120">Microsoft XPS Document Writer</span></span>](/windows/win32/printdocs/microsoft-xps-document-writer)
