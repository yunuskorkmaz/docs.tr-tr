---
title: PrintDialog Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0ed7f7a1f9770f71b75ae744a056b6943335c852
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728671"
---
# <a name="printdialog-component-overview-windows-forms"></a><span data-ttu-id="50f70-102">PrintDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="50f70-102">PrintDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="50f70-103">Windows Forms [PrintDialog](printdialog-component-windows-forms.md) bileşeni, bir yazıcı seçmek, yazdırılacak sayfaları seçmek ve Windows tabanlı uygulamalarda yazdırma ile ilgili diğer ayarları belirlemek için kullanılan önceden yapılandırılmış bir iletişim kutusudur.</span><span class="sxs-lookup"><span data-stu-id="50f70-103">The Windows Forms [PrintDialog](printdialog-component-windows-forms.md) component is a pre-configured dialog box used to select a printer, choose the pages to print, and determine other print-related settings in Windows-based applications.</span></span> <span data-ttu-id="50f70-104">Kendi iletişim kutusunu yapılandırmak yerine yazıcı ve yazdırma ile ilgili ayarlar için basit bir çözüm olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="50f70-104">Use it as a simple solution for printer and print-related settings selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="50f70-105">Kullanıcıların belgelerinin birçok bölümünü yazdırmasını sağlayabilirsiniz: tümünü yazdır, seçili sayfa aralığını Yazdır veya bir seçimi yazdır.</span><span class="sxs-lookup"><span data-stu-id="50f70-105">You can enable users to print many parts of their documents: print all, print a selected page range, or print a selection.</span></span> <span data-ttu-id="50f70-106">Standart Windows iletişim kutularına bağlı olarak, temel işlevselliği kullanıcılara hemen tanıdık olan uygulamalar oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="50f70-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="50f70-107"><xref:System.Windows.Forms.PrintDialog> bileşen <xref:System.Windows.Forms.CommonDialog> sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="50f70-107">The <xref:System.Windows.Forms.PrintDialog> component inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="working-with-the-component"></a><span data-ttu-id="50f70-108">Bileşenle çalışma</span><span class="sxs-lookup"><span data-stu-id="50f70-108">Working with the Component</span></span>

<span data-ttu-id="50f70-109">Çalışma zamanında iletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="50f70-109">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="50f70-110">Bu bileşen, tek bir yazdırma işiyle (<xref:System.Drawing.Printing.PrintDocument> sınıfı) veya tek bir yazıcının (<xref:System.Drawing.Printing.PrinterSettings> sınıfının) ayarlarıyla ilgili özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="50f70-110">This component has properties that relate to either a single print job (<xref:System.Drawing.Printing.PrintDocument> class) or the settings of an individual printer (<xref:System.Drawing.Printing.PrinterSettings> class).</span></span> <span data-ttu-id="50f70-111">Bunlardan biri sırasıyla birden çok yazıcı tarafından paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="50f70-111">Either of these, in turn, may be shared by multiple printers.</span></span>

<span data-ttu-id="50f70-112">Bir forma eklendiğinde <xref:System.Windows.Forms.PrintDialog> bileşeni, Visual Studio 'daki Windows Form Tasarımcısı alt kısmındaki tepside görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="50f70-112">When it is added to a form, the <xref:System.Windows.Forms.PrintDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="50f70-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50f70-113">See also</span></span>

- <xref:System.Windows.Forms.PrintDialog>
- [<span data-ttu-id="50f70-114">PrintDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="50f70-114">PrintDialog Component</span></span>](printdialog-component-windows-forms.md)
