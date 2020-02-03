---
title: PageSetupDialog Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: a891cb8cc77007d7591d41461c94f61c077eb300
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744334"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a><span data-ttu-id="fdbf9-102">PageSetupDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fdbf9-102">PageSetupDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="fdbf9-103">Windows Forms <xref:System.Windows.Forms.PageSetupDialog> bileşeni, Windows tabanlı uygulamalarda yazdırma için sayfa ayrıntılarını ayarlamak üzere kullanılan önceden yapılandırılmış bir iletişim kutusudur.</span><span class="sxs-lookup"><span data-stu-id="fdbf9-103">The Windows Forms <xref:System.Windows.Forms.PageSetupDialog> component is a pre-configured dialog box used to set page details for printing in Windows-based applications.</span></span> <span data-ttu-id="fdbf9-104">Kullanıcıların kendi iletişim kutusunu yapılandırmak yerine sayfa tercihleri ayarlamak için Windows tabanlı uygulamanızda bu uygulamayı basit bir çözüm olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="fdbf9-104">Use it within your Windows-based application as a simple solution for users to set page preferences in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="fdbf9-105">Kullanıcıların kenarlık ve kenar boşluğu ayarlamalarını, üst bilgileri ve altbilgileri ve dikey ya da yatay yönlendirmeyi ayarlamasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdbf9-105">You can enable users to set border and margin adjustments, headers and footers, and portrait or landscape orientation.</span></span> <span data-ttu-id="fdbf9-106">Standart Windows iletişim kutularına bağlı olarak, temel işlevselliği kullanıcılara hemen tanıdık olan uygulamalar oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="fdbf9-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="fdbf9-107">Anahtar özellikleri ve yöntemleri</span><span class="sxs-lookup"><span data-stu-id="fdbf9-107">Key Properties and Methods</span></span>

<span data-ttu-id="fdbf9-108">Çalışma zamanında iletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fdbf9-108">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="fdbf9-109">Bu bileşen, tek bir sayfa (<xref:System.Drawing.Printing.PrintDocument> sınıfı) veya herhangi bir belge (<xref:System.Drawing.Printing.PageSettings> sınıfı) ile ilgili olarak ayarlayabileceğiniz özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fdbf9-109">This component has properties you can set that relate to either a single page (<xref:System.Drawing.Printing.PrintDocument> class) or any document (<xref:System.Drawing.Printing.PageSettings> class).</span></span> <span data-ttu-id="fdbf9-110">Ayrıca, <xref:System.Windows.Forms.PageSetupDialog> bileşeni, <xref:System.Drawing.Printing.PrinterSettings> sınıfında depolanan belirli yazıcı ayarlarını belirlemede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdbf9-110">Additionally, the <xref:System.Windows.Forms.PageSetupDialog> component can be used to determine specific printer settings, which are stored in the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span>

<span data-ttu-id="fdbf9-111">Bir forma eklendiğinde <xref:System.Windows.Forms.PageSetupDialog> bileşeni, Visual Studio 'daki Windows Form Tasarımcısı alt kısmındaki tepside görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fdbf9-111">When it is added to a form, the <xref:System.Windows.Forms.PageSetupDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="fdbf9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdbf9-112">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="fdbf9-113">PageSetupDialog bileşeni</span><span class="sxs-lookup"><span data-stu-id="fdbf9-113">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)
