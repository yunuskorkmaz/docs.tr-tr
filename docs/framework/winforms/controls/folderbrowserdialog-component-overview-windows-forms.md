---
title: FolderBrowserDialog bileşenine genel bakış
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: 8b017ba08ae4205e930ac00177c89a89fde17d3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745731"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a><span data-ttu-id="02daa-102">FolderBrowserDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="02daa-102">FolderBrowserDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="02daa-103">Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni, klasörlere göz atmak ve klasörler seçmek için kullanılan bir kalıcı iletişim kutusudur.</span><span class="sxs-lookup"><span data-stu-id="02daa-103">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component is a modal dialog box that is used for browsing and selecting folders.</span></span> <span data-ttu-id="02daa-104">Yeni klasörler, <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni içinden de oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="02daa-104">New folders can also be created from within the <xref:System.Windows.Forms.FolderBrowserDialog> component.</span></span>

> [!NOTE]
> <span data-ttu-id="02daa-105">Klasörler yerine dosyaları seçmek için [OpenFileDialog](openfiledialog-component-windows-forms.md) bileşenini kullanın.</span><span class="sxs-lookup"><span data-stu-id="02daa-105">To select files, instead of folders, use the [OpenFileDialog](openfiledialog-component-windows-forms.md) component.</span></span>

<span data-ttu-id="02daa-106"><xref:System.Windows.Forms.FolderBrowserDialog> bileşeni, <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi kullanılarak çalışma zamanında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="02daa-106">The <xref:System.Windows.Forms.FolderBrowserDialog> component is displayed at run time using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="02daa-107">En üstteki klasörü ve iletişim kutusunun ağaç görünümünde görünecek alt klasörleri öğrenmek için <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="02daa-107">Set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property to determine the top-most folder and any subfolders that will appear within the tree view of the dialog box.</span></span> <span data-ttu-id="02daa-108">İletişim kutusu gösterildikten sonra, seçilen klasörün yolunu almak için <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02daa-108">Once the dialog box has been shown, you can use the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property to get the path of the folder that was selected.</span></span>

<span data-ttu-id="02daa-109">Bir forma eklendiğinde <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni, Visual Studio 'daki Windows Form Tasarımcısı alt kısmındaki tepside görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="02daa-109">When it is added to a form, the <xref:System.Windows.Forms.FolderBrowserDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="02daa-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02daa-110">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="02daa-111">Nasıl yapılır: Windows Forms FolderBrowserDialog Bileşeni ile Klasörleri Seçme</span><span class="sxs-lookup"><span data-stu-id="02daa-111">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [<span data-ttu-id="02daa-112">FolderBrowserDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="02daa-112">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
