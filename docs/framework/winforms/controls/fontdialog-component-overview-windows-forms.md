---
title: FontDialog Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 7f140807bf4b42e530302190042e729c59248e7f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098565"
---
# <a name="fontdialog-component-overview-windows-forms"></a><span data-ttu-id="a0491-102">FontDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a0491-102">FontDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="a0491-103">Windows Forms <xref:System.Windows.Forms.FontDialog> bileşendir standart Windows olan bir önceden yapılandırılmış bir iletişim kutusu **yazı tipi** sistemde yüklü yazı tiplerini kullanıma sunmak için kullanılan iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="a0491-103">The Windows Forms <xref:System.Windows.Forms.FontDialog> component is a pre-configured dialog box, which is the standard Windows **Font** dialog box used to expose the fonts that are currently installed on the system.</span></span> <span data-ttu-id="a0491-104">Basit bir çözüm olarak, Windows tabanlı uygulama içindeki yazı tipi seçimi yerine kendi iletişim kutusu yapılandırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0491-104">Use it within your Windows-based application as a simple solution for font selection in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="a0491-105">Varsayılan olarak, liste kutuları iletişim kutusu, yazı tipi için gösterir. yazı tipi stili ve boyutu; üstü çizili ve alt çizgi gibi etkileri için onay kutularını; komut dosyası için bir açılan liste; ve yazı tipi nasıl görüneceğini gösteren bir örnek.</span><span class="sxs-lookup"><span data-stu-id="a0491-105">By default, the dialog box shows list boxes for Font, Font style, and Size; check boxes for effects like Strikeout and Underline; a drop-down list for Script; and a sample of how the font will appear.</span></span> <span data-ttu-id="a0491-106">(Betik belirli bir yazı tipi için kullanılabilen farklı karakter betikleri gibi İbranice veya Japonca ifade eder.) Yazı tipi iletişim kutusu görüntülemek için çağrı <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a0491-106">(Script refers to different character scripts that are available for a given font, for example, Hebrew or Japanese.) To display the font dialog box, call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="a0491-107">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="a0491-107">Key Properties</span></span>  
 <span data-ttu-id="a0491-108">Bileşen bir dizi görünümünü Yapılandırma özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="a0491-108">The component has a number of properties that configure its appearance.</span></span> <span data-ttu-id="a0491-109">İletişim kutusu seçimleri ayarlama özellikleri <xref:System.Windows.Forms.FontDialog.Font%2A> ve <xref:System.Windows.Forms.FontDialog.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="a0491-109">The properties that set the dialog-box selections are <xref:System.Windows.Forms.FontDialog.Font%2A> and <xref:System.Windows.Forms.FontDialog.Color%2A>.</span></span> <span data-ttu-id="a0491-110"><xref:System.Windows.Forms.FontDialog.Font%2A> Özelliğini ayarlar yazı tipini, stili, boyutunu, betik ve etkiler; Örneğin, `Arial, 10pt, style=Italic, Strikeout`.</span><span class="sxs-lookup"><span data-stu-id="a0491-110">The <xref:System.Windows.Forms.FontDialog.Font%2A> property sets the font, style, size, script, and effects; for example, `Arial, 10pt, style=Italic, Strikeout`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0491-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0491-111">See also</span></span>

- <xref:System.Windows.Forms.FontDialog>
- [<span data-ttu-id="a0491-112">FontDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="a0491-112">FontDialog Component</span></span>](fontdialog-component-windows-forms.md)
