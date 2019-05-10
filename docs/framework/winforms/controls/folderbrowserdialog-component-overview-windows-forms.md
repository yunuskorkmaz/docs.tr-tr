---
title: FolderBrowserDialog Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: cd89980ccad7e6c73094c1fb462d93cee8094959
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210407"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a><span data-ttu-id="2122e-102">FolderBrowserDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2122e-102">FolderBrowserDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="2122e-103">Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> klasörleri seçme ve Tarama için kullanılan kalıcı bir iletişim kutusu bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="2122e-103">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component is a modal dialog box that is used for browsing and selecting folders.</span></span> <span data-ttu-id="2122e-104">Yeni klasörler de oluşturulabilir içinden <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="2122e-104">New folders can also be created from within the <xref:System.Windows.Forms.FolderBrowserDialog> component.</span></span>

> [!NOTE]
> <span data-ttu-id="2122e-105">Dosyaları, klasörleri, yerine seçmek için kullanın [OpenFileDialog](openfiledialog-component-windows-forms.md) bileşeni.</span><span class="sxs-lookup"><span data-stu-id="2122e-105">To select files, instead of folders, use the [OpenFileDialog](openfiledialog-component-windows-forms.md) component.</span></span>

<span data-ttu-id="2122e-106"><xref:System.Windows.Forms.FolderBrowserDialog> Bileşeni kullanarak çalışma zamanında görüntülenen <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2122e-106">The <xref:System.Windows.Forms.FolderBrowserDialog> component is displayed at run time using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="2122e-107">Ayarlama <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> en üst klasörü ve iletişim kutusunun ağacı görünümü içinde görünecek tüm alt klasörleri belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="2122e-107">Set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property to determine the top-most folder and any subfolders that will appear within the tree view of the dialog box.</span></span> <span data-ttu-id="2122e-108">İletişim kutusunda gösterilen sonra kullanabileceğiniz <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> seçilen klasörün yolunu almak için özellik.</span><span class="sxs-lookup"><span data-stu-id="2122e-108">Once the dialog box has been shown, you can use the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property to get the path of the folder that was selected.</span></span>

<span data-ttu-id="2122e-109">Bir forma eklendiğinde <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni Tepsi Visual Studio'da Windows Form Tasarımcısı'nın altındaki görünür.</span><span class="sxs-lookup"><span data-stu-id="2122e-109">When it is added to a form, the <xref:System.Windows.Forms.FolderBrowserDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="2122e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2122e-110">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="2122e-111">Nasıl yapılır: Windows Forms FolderBrowserDialog bileşeni ile klasörleri seçin</span><span class="sxs-lookup"><span data-stu-id="2122e-111">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [<span data-ttu-id="2122e-112">FolderBrowserDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="2122e-112">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
