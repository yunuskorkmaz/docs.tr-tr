---
title: SaveFileDialog Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 1e4269129f17c10056af2765c7a0e74537918ae5
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211615"
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="d262b-102">SaveFileDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d262b-102">SaveFileDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="d262b-103">Windows Forms <xref:System.Windows.Forms.SaveFileDialog> bir önceden yapılandırılmış bir iletişim kutusu bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="d262b-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="d262b-104">Standart ile aynı olduğu **dosyayı Kaydet** Windows tarafından kullanılan iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d262b-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="d262b-105">Devraldığı <xref:System.Windows.Forms.CommonDialog> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d262b-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="d262b-106">SaveFileDialog bileşeni ile çalışma</span><span class="sxs-lookup"><span data-stu-id="d262b-106">Working with the SaveFileDialog Component</span></span>

<span data-ttu-id="d262b-107">Basit bir çözüm, kullanıcıların kendi iletişim kutusu yapılandırmak yerine dosyaları kaydetmeyi etkinleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d262b-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="d262b-108">Standart Windows iletişim kutularında bağlı olan temel işlevleri oluşturduğunuz uygulamaların kullanıcılarına hemen tanıdık gelir.</span><span class="sxs-lookup"><span data-stu-id="d262b-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="d262b-109">Ancak, unutmayın olduğunda kullanarak <xref:System.Windows.Forms.SaveFileDialog> bileşeni, kendi dosya kaydetme mantıksal yazmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d262b-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>

<span data-ttu-id="d262b-110">Kullanabileceğiniz <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d262b-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="d262b-111">Okuma/yazma modu kullanarak bir dosyayı açabilirsiniz <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d262b-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>

<span data-ttu-id="d262b-112">Bir forma eklendiğinde <xref:System.Windows.Forms.SaveFileDialog> bileşeni Tepsi Visual Studio'da Windows Form Tasarımcısı'nın altındaki görünür.</span><span class="sxs-lookup"><span data-stu-id="d262b-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="d262b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d262b-113">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="d262b-114">SaveFileDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="d262b-114">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
