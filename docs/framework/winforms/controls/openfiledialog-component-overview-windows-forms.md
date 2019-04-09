---
title: OpenFileDialog Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: ec275a5923d332d23205c79442fa23bc6e402e3f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147348"
---
# <a name="openfiledialog-component-overview-windows-forms"></a><span data-ttu-id="be970-102">OpenFileDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="be970-102">OpenFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="be970-103">Windows Forms <xref:System.Windows.Forms.OpenFileDialog> bir önceden yapılandırılmış bir iletişim kutusu bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="be970-103">The Windows Forms <xref:System.Windows.Forms.OpenFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="be970-104">Aynı olan **açık dosya** Windows işletim sistemi tarafından kullanıma sunulan iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="be970-104">It is the same **Open File** dialog box exposed by the Windows operating system.</span></span> <span data-ttu-id="be970-105">Devraldığı <xref:System.Windows.Forms.CommonDialog> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="be970-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="using-this-component"></a><span data-ttu-id="be970-106">Bu bileşeni kullanma</span><span class="sxs-lookup"><span data-stu-id="be970-106">Using this Component</span></span>  
 <span data-ttu-id="be970-107">Bu bileşen, Windows tabanlı bir uygulama içinde kendi iletişim kutusu yapılandırma yerine dosya seçimi için basit bir çözüm kullanın.</span><span class="sxs-lookup"><span data-stu-id="be970-107">Use this component within your Windows-based application as a simple solution for file selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="be970-108">Standart Windows iletişim kutularında bağlı olarak, temel işlevleri kullanıcılarına hemen tanıdık uygulamalar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="be970-108">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="be970-109">Ancak, unutmayın olduğunda kullanarak <xref:System.Windows.Forms.OpenFileDialog> bileşeni, kendi dosya açma mantığı yazmalıdır.</span><span class="sxs-lookup"><span data-stu-id="be970-109">Be aware, however, that when using the <xref:System.Windows.Forms.OpenFileDialog> component, you must write your own file-opening logic.</span></span>  
  
 <span data-ttu-id="be970-110">Kullanım <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="be970-110">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="be970-111">Çoklu seçim ile açılmasını dosyaya kullanıcılara etkinleştirebilirsiniz <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="be970-111">You can enable users to multi-select files to be opened with the <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> property.</span></span> <span data-ttu-id="be970-112">Ayrıca, kullanabileceğiniz <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> özelliği salt okunur bir onay kutusu iletişim kutusunda görünüp görünmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="be970-112">Additionally, you can use the <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> property to determine if a read-only check box appears in the dialog box.</span></span> <span data-ttu-id="be970-113"><xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> Özelliği salt okunur onay kutusunun seçili olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="be970-113">The <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> property indicates whether the read-only check box is selected.</span></span> <span data-ttu-id="be970-114">Son olarak, <xref:System.Windows.Forms.FileDialog.Filter%2A> özelliğini ayarlar iletişim kutusundaki "Dosya türü" görünen seçenekler belirleyen geçerli dosya adı filtre dizesi,.</span><span class="sxs-lookup"><span data-stu-id="be970-114">Finally, the <xref:System.Windows.Forms.FileDialog.Filter%2A> property sets the current file name filter string, which determines the choices that appear in the "Files of type" box in the dialog box.</span></span>  
  
 <span data-ttu-id="be970-115">Bir forma eklendiğinde <xref:System.Windows.Forms.OpenFileDialog> bileşeni Tepsi Windows Form Tasarımcısı'nın altındaki görünür.</span><span class="sxs-lookup"><span data-stu-id="be970-115">When it is added to a form, the <xref:System.Windows.Forms.OpenFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be970-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be970-116">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="be970-117">OpenFileDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="be970-117">OpenFileDialog Component</span></span>](openfiledialog-component-windows-forms.md)
