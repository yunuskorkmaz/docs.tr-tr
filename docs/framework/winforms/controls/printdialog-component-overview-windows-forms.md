---
title: PrintDialog Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: dfd6979c596f47fbc9bf68e3866f7fbc9d1dc21c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723367"
---
# <a name="printdialog-component-overview-windows-forms"></a><span data-ttu-id="6b2cb-102">PrintDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6b2cb-102">PrintDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="6b2cb-103">Windows Forms [PrintDialog](printdialog-component-windows-forms.md) bir yazıcı seçin, yazdırılacak sayfa seçin ve diğer Windows tabanlı uygulamalar ile ilgili ayarları belirlemek için kullanılan bir önceden yapılandırılmış bir iletişim kutusu bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="6b2cb-103">The Windows Forms [PrintDialog](printdialog-component-windows-forms.md) component is a pre-configured dialog box used to select a printer, choose the pages to print, and determine other print-related settings in Windows-based applications.</span></span> <span data-ttu-id="6b2cb-104">Yazıcı ve yazdırma ile ilgili ayarları Seçimi'yerine kendi iletişim kutusunu yapılandırma için basit bir çözüm kullanın.</span><span class="sxs-lookup"><span data-stu-id="6b2cb-104">Use it as a simple solution for printer and print-related settings selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="6b2cb-105">Kullanıcılar kendi belgeleri pek çok bölümünün yazdırmak etkinleştirebilirsiniz: tüm yazdırma, yazdırma seçili sayfa aralığı veya bir seçim yazdırma.</span><span class="sxs-lookup"><span data-stu-id="6b2cb-105">You can enable users to print many parts of their documents: print all, print a selected page range, or print a selection.</span></span> <span data-ttu-id="6b2cb-106">Standart Windows iletişim kutularında bağlı olarak, temel işlevleri kullanıcılarına hemen tanıdık uygulamalar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6b2cb-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="6b2cb-107"><xref:System.Windows.Forms.PrintDialog> Bileşeni devraldığı <xref:System.Windows.Forms.CommonDialog> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6b2cb-107">The <xref:System.Windows.Forms.PrintDialog> component inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-component"></a><span data-ttu-id="6b2cb-108">Bileşeni ile çalışma</span><span class="sxs-lookup"><span data-stu-id="6b2cb-108">Working with the Component</span></span>  
 <span data-ttu-id="6b2cb-109">Kullanım <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6b2cb-109">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="6b2cb-110">Bu bileşen için ya da tek bir yazdırma işi ile ilgili özellikleri vardır (<xref:System.Drawing.Printing.PrintDocument> sınıfı) veya ayrı bir yazıcı ayarlarını (<xref:System.Drawing.Printing.PrinterSettings> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="6b2cb-110">This component has properties that relate to either a single print job (<xref:System.Drawing.Printing.PrintDocument> class) or the settings of an individual printer (<xref:System.Drawing.Printing.PrinterSettings> class).</span></span> <span data-ttu-id="6b2cb-111">Bunlardan biri, buna karşılık, birden çok yazıcılar tarafından paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="6b2cb-111">Either of these, in turn, may be shared by multiple printers.</span></span>  
  
 <span data-ttu-id="6b2cb-112">Bir forma eklendiğinde <xref:System.Windows.Forms.PrintDialog> bileşeni Tepsi Windows Form Tasarımcısı'nın altındaki görünür.</span><span class="sxs-lookup"><span data-stu-id="6b2cb-112">When it is added to a form, the <xref:System.Windows.Forms.PrintDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b2cb-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b2cb-113">See also</span></span>
- <xref:System.Windows.Forms.PrintDialog>
- [<span data-ttu-id="6b2cb-114">PrintDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="6b2cb-114">PrintDialog Component</span></span>](printdialog-component-windows-forms.md)
