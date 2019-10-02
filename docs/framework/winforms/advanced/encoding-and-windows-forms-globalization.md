---
title: Kodlama ve Windows Forms Genelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], lack of Unicode support
- DateTimePicker control [Windows Forms], lack of Unicode support
- TrackBar control [Windows Forms], lack of Unicode support
- ImageList component [Windows Forms], lack of Unicode support
- Unicode [Windows Forms]
- ToolBar control [Windows Forms], lack of Unicode support
- international applications [Windows Forms], character display
- StatusBar control [Windows Forms], lack of Unicode support
- MonthCalendar control [Windows Forms], lack of Unicode support
- international characters
- TabControl control [Windows Forms], lack of Unicode support
- Windows Forms, encoding
- TreeView control [Windows Forms], lack of Unicode support
- ProgressBar control [Windows Forms], Unicode-enabled forms
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: 22e8965d-a712-42b3-8167-3ee346bd70f9
ms.openlocfilehash: 60ca9f7ba2f716b5dab1b0276bc3cd07ddd8f65c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736880"
---
# <a name="encoding-and-windows-forms-globalization"></a><span data-ttu-id="d20b1-102">Kodlama ve Windows Forms Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="d20b1-102">Encoding and Windows Forms Globalization</span></span>

<span data-ttu-id="d20b1-103">Windows Forms uygulamalar tamamen Unicode özellikli olduğundan, her karakterin platform, program veya dile bakılmaksızın benzersiz bir sayıyla temsil edildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d20b1-103">Windows Forms applications are entirely Unicode-enabled, meaning that each character is represented by a unique number, no matter what the platform, program, or language.</span></span> <span data-ttu-id="d20b1-104">Unicode hakkında daha fazla bilgi için bkz. [Unicode konsorsiyum Web sitesi](https://www.unicode.org).</span><span class="sxs-lookup"><span data-stu-id="d20b1-104">For more information about Unicode, see the [Unicode consortium Web site](https://www.unicode.org).</span></span>

## <a name="benefits-of-unicode"></a><span data-ttu-id="d20b1-105">Unicode avantajları</span><span class="sxs-lookup"><span data-stu-id="d20b1-105">Benefits of Unicode</span></span>

<span data-ttu-id="d20b1-106">Unicode özellikli formların avantajları, Hintçe gibi yalnızca Unicode olan betiklerle çalışma olanağını içerir.</span><span class="sxs-lookup"><span data-stu-id="d20b1-106">The benefits of Unicode-enabled forms include the ability to work with scripts that are Unicode-only, such as Hindi.</span></span> <span data-ttu-id="d20b1-107">Ayrıca, tek bir biçimde birden çok dil kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d20b1-107">In addition, you can use multiple languages on a single form.</span></span> <span data-ttu-id="d20b1-108">Unicode 'da, tüm karakterler iki bayt uzunluğundadır, bu nedenle çift baytlık karakterleri temsil etmek için özel bir çaba gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d20b1-108">In Unicode, all characters are two bytes long, so no special effort is needed to represent double-byte characters.</span></span> <span data-ttu-id="d20b1-109">Ayrıca, tüm platformlarda çalışacak tek bir kod kümesi de yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d20b1-109">You can also write a single set of code that will work on all platforms.</span></span> <span data-ttu-id="d20b1-110">Bu, önceki Visual Basic sürümlerinden bir değişiklik olduğundan, Windows NT ve Windows 98 gibi farklı platformlar için farklı kodlar yazmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="d20b1-110">This is a change from previous versions of Visual Basic, in which you had to write different code for different platforms, such as Windows NT and Windows 98.</span></span>

<span data-ttu-id="d20b1-111">Ancak, bazı denetimler Windows 98 ve Windows Millennium Edition 'da Unicode 'U desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d20b1-111">However, certain controls do not support Unicode in Windows 98 and Windows Millennium Edition.</span></span> <span data-ttu-id="d20b1-112">Bu denetimler, tüm ortak denetimden devraldığı, ANSI olarak Windows kod sayfalarıyla verileri işleyecek.</span><span class="sxs-lookup"><span data-stu-id="d20b1-112">These controls, all of which inherit from the common control, will process data with the Windows code pages, as ANSI.</span></span> <span data-ttu-id="d20b1-113">Bu denetimler şunlardır: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar> ve <xref:System.Windows.Forms.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="d20b1-113">These controls are: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, and <xref:System.Windows.Forms.StatusBar>.</span></span> <span data-ttu-id="d20b1-114">Sonuç olarak, listelenen platformlarda Unicode verilerini bu denetimlerde görüntüleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d20b1-114">As a result, you cannot display Unicode data in these controls on the listed platforms.</span></span> <span data-ttu-id="d20b1-115">Örneğin, Ingilizce bir Windows 98 işletim sisteminde Japonca karakterler görüntüleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d20b1-115">For example, you cannot display Japanese characters on an English Windows 98 operating system.</span></span>

<span data-ttu-id="d20b1-116">@No__t-0 ve <xref:System.Windows.Forms.StatusBar> denetimlerinin Unicode kullanan alternatifleri için, bu eski denetimleri değiştirecek <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.StatusStrip> denetimlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d20b1-116">For Unicode-aware alternatives to the <xref:System.Windows.Forms.ToolBar> and <xref:System.Windows.Forms.StatusBar> controls, use the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip> controls, which replace these older controls.</span></span> <span data-ttu-id="d20b1-117">Uygulamanızdaki görsel öğeler arasında benzer bir görünüm sağlamak için, <xref:System.Windows.Forms.MainMenu> yerine işleme menüleri için <xref:System.Windows.Forms.MenuStrip> denetimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d20b1-117">To maintain a similar look and feel between visual elements in your application, use the <xref:System.Windows.Forms.MenuStrip> control for rendering menus instead of <xref:System.Windows.Forms.MainMenu>.</span></span> <span data-ttu-id="d20b1-118">@No__t-0 ve <xref:System.Windows.Forms.StatusStrip> gibi <xref:System.Windows.Forms.MenuStrip> de Unicode karakterleri işleyebilir ve görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="d20b1-118">Like <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> can also process and display Unicode characters.</span></span>

## <a name="see-also"></a><span data-ttu-id="d20b1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d20b1-119">See also</span></span>

- [<span data-ttu-id="d20b1-120">Windows Forms uygulamaları Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="d20b1-120">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)
