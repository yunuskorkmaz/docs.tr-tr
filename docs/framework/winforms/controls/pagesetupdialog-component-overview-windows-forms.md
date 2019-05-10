---
title: PageSetupDialog Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: 989183b6152dfccb6167d89433317cea596d83c5
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211737"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a><span data-ttu-id="cfb9a-102">PageSetupDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="cfb9a-102">PageSetupDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="cfb9a-103">Windows Forms <xref:System.Windows.Forms.PageSetupDialog> sayfa ayrıntıları yazdırma için Windows tabanlı uygulamalar ayarlamak için kullanılan bir önceden yapılandırılmış bir iletişim kutusu bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="cfb9a-103">The Windows Forms <xref:System.Windows.Forms.PageSetupDialog> component is a pre-configured dialog box used to set page details for printing in Windows-based applications.</span></span> <span data-ttu-id="cfb9a-104">Windows tabanlı uygulamanızda basit bir çözüm olarak kullanıcılar yerine kendi iletişim kutusu yapılandırma sayfası tercihleri ayarlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfb9a-104">Use it within your Windows-based application as a simple solution for users to set page preferences in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="cfb9a-105">Kenarlık ve kenar boşluğu ayarlamaları, üstbilgiler, altbilgiler ve dikey veya yatay hizalama ayarlamak kullanıcıların etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfb9a-105">You can enable users to set border and margin adjustments, headers and footers, and portrait or landscape orientation.</span></span> <span data-ttu-id="cfb9a-106">Standart Windows iletişim kutularında bağlı olarak, temel işlevleri kullanıcılarına hemen tanıdık uygulamalar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cfb9a-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="cfb9a-107">Anahtar özellikleri ve yöntemleri</span><span class="sxs-lookup"><span data-stu-id="cfb9a-107">Key Properties and Methods</span></span>

<span data-ttu-id="cfb9a-108">Kullanım <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cfb9a-108">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="cfb9a-109">Bu bileşen için ya da tek bir sayfayla ilişkili ayarlayabileceğiniz özelliklerine sahip (<xref:System.Drawing.Printing.PrintDocument> sınıfı) veya herhangi bir belge (<xref:System.Drawing.Printing.PageSettings> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="cfb9a-109">This component has properties you can set that relate to either a single page (<xref:System.Drawing.Printing.PrintDocument> class) or any document (<xref:System.Drawing.Printing.PageSettings> class).</span></span> <span data-ttu-id="cfb9a-110">Ayrıca, <xref:System.Windows.Forms.PageSetupDialog> bileşeni, depolanmış belirli bir yazıcı ayarlarını belirlemek için kullanılabilir <xref:System.Drawing.Printing.PrinterSettings> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cfb9a-110">Additionally, the <xref:System.Windows.Forms.PageSetupDialog> component can be used to determine specific printer settings, which are stored in the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span>

<span data-ttu-id="cfb9a-111">Bir forma eklendiğinde <xref:System.Windows.Forms.PageSetupDialog> bileşeni Tepsi Visual Studio'da Windows Form Tasarımcısı'nın altındaki görünür.</span><span class="sxs-lookup"><span data-stu-id="cfb9a-111">When it is added to a form, the <xref:System.Windows.Forms.PageSetupDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfb9a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfb9a-112">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="cfb9a-113">PageSetupDialog bileşeni</span><span class="sxs-lookup"><span data-stu-id="cfb9a-113">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)
