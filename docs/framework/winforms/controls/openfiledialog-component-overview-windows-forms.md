---
title: OpenFileDialog Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: c519b373150a49ee41dbb0c503f7d5a4862477d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728442"
---
# <a name="openfiledialog-component-overview-windows-forms"></a><span data-ttu-id="ee9b8-102">OpenFileDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ee9b8-102">OpenFileDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="ee9b8-103">Windows Forms <xref:System.Windows.Forms.OpenFileDialog> bileşeni önceden yapılandırılmış bir iletişim kutusudur.</span><span class="sxs-lookup"><span data-stu-id="ee9b8-103">The Windows Forms <xref:System.Windows.Forms.OpenFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="ee9b8-104">Windows işletim sistemi tarafından kullanıma sunulan aynı **Açık dosya** iletişim kutusudur.</span><span class="sxs-lookup"><span data-stu-id="ee9b8-104">It is the same **Open File** dialog box exposed by the Windows operating system.</span></span> <span data-ttu-id="ee9b8-105"><xref:System.Windows.Forms.CommonDialog> sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="ee9b8-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="use-this-component"></a><span data-ttu-id="ee9b8-106">Bu bileşeni kullan</span><span class="sxs-lookup"><span data-stu-id="ee9b8-106">Use this component</span></span>

<span data-ttu-id="ee9b8-107">Bu bileşeni, kendi iletişim kutusunu yapılandırmak yerine, dosya seçimi için basit bir çözüm olarak Windows tabanlı uygulamanızda kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee9b8-107">Use this component within your Windows-based application as a simple solution for file selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="ee9b8-108">Standart Windows iletişim kutularına bağlı olarak, temel işlevselliği kullanıcılara hemen tanıdık olan uygulamalar oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="ee9b8-108">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="ee9b8-109">Ancak <xref:System.Windows.Forms.OpenFileDialog> bileşeni kullanılırken kendi dosya açma mantığınızı yazmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ee9b8-109">Be aware, however, that when using the <xref:System.Windows.Forms.OpenFileDialog> component, you must write your own file-opening logic.</span></span>

<span data-ttu-id="ee9b8-110">Çalışma zamanında iletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee9b8-110">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="ee9b8-111">Kullanıcıların <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> özelliği ile açılacak birden çok seçim dosyaları sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee9b8-111">You can enable users to multi-select files to be opened with the <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> property.</span></span> <span data-ttu-id="ee9b8-112">Ayrıca, iletişim kutusunda salt okuma onay kutusunun görünüp göründüğünü anlamak için <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee9b8-112">Additionally, you can use the <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> property to determine if a read-only check box appears in the dialog box.</span></span> <span data-ttu-id="ee9b8-113"><xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> özelliği salt okunurdur onay kutusunun seçili olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee9b8-113">The <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> property indicates whether the read-only check box is selected.</span></span> <span data-ttu-id="ee9b8-114">Son olarak, <xref:System.Windows.Forms.FileDialog.Filter%2A> özelliği, iletişim kutusundaki "tür dosyaları" kutusunda görünen seçimleri belirleyen geçerli dosya adı filtre dizesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ee9b8-114">Finally, the <xref:System.Windows.Forms.FileDialog.Filter%2A> property sets the current file name filter string, which determines the choices that appear in the "Files of type" box in the dialog box.</span></span>

<span data-ttu-id="ee9b8-115">Bir forma eklendiğinde <xref:System.Windows.Forms.OpenFileDialog> bileşeni, Visual Studio 'daki Windows Form Tasarımcısı alt kısmındaki tepside görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ee9b8-115">When it is added to a form, the <xref:System.Windows.Forms.OpenFileDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee9b8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee9b8-116">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="ee9b8-117">OpenFileDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="ee9b8-117">OpenFileDialog Component</span></span>](openfiledialog-component-windows-forms.md)
