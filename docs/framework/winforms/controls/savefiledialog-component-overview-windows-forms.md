---
title: SaveFileDialog Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 7609c29b7e932ecee7dc8a289617094bd8d480e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743104"
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="e0993-102">SaveFileDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e0993-102">SaveFileDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="e0993-103">Windows Forms <xref:System.Windows.Forms.SaveFileDialog> bileşeni önceden yapılandırılmış bir iletişim kutusudur.</span><span class="sxs-lookup"><span data-stu-id="e0993-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="e0993-104">Windows tarafından kullanılan standart **Dosya Kaydet** iletişim kutusuyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e0993-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="e0993-105"><xref:System.Windows.Forms.CommonDialog> sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="e0993-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="e0993-106">SaveFileDialog bileşeniyle çalışma</span><span class="sxs-lookup"><span data-stu-id="e0993-106">Working with the SaveFileDialog Component</span></span>

<span data-ttu-id="e0993-107">Bu uygulamayı, kullanıcıların kendi iletişim kutusunu yapılandırmak yerine dosyaları kaydetmesine olanak tanımak için basit bir çözüm olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0993-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="e0993-108">Standart Windows iletişim kutularına bağlı olarak, oluşturduğunuz uygulamaların temel işlevleri kullanıcılara hemen tanıdık gelecektir.</span><span class="sxs-lookup"><span data-stu-id="e0993-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="e0993-109">Ancak, <xref:System.Windows.Forms.SaveFileDialog> bileşenini kullanırken kendi dosya kaydetme mantığınızı yazmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e0993-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>

<span data-ttu-id="e0993-110">Çalışma zamanında iletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0993-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="e0993-111"><xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> yöntemi kullanarak okuma/yazma modunda bir dosya açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0993-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>

<span data-ttu-id="e0993-112">Bir forma eklendiğinde <xref:System.Windows.Forms.SaveFileDialog> bileşeni, Visual Studio 'daki Windows Form Tasarımcısı alt kısmındaki tepside görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e0993-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0993-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0993-113">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="e0993-114">SaveFileDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="e0993-114">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
