---
title: FontDialog Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 664b756dc068ca283e4f43edbdd0f3266f5d1142
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745697"
---
# <a name="fontdialog-component-overview-windows-forms"></a><span data-ttu-id="b2d8e-102">FontDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b2d8e-102">FontDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="b2d8e-103">Windows Forms <xref:System.Windows.Forms.FontDialog> bileşeni, sistemde yüklü olan yazı tiplerini açığa çıkarmak için kullanılan standart Windows **yazı tipi** iletişim kutusu olan önceden yapılandırılmış bir iletişim kutusudur.</span><span class="sxs-lookup"><span data-stu-id="b2d8e-103">The Windows Forms <xref:System.Windows.Forms.FontDialog> component is a pre-configured dialog box, which is the standard Windows **Font** dialog box used to expose the fonts that are currently installed on the system.</span></span> <span data-ttu-id="b2d8e-104">Kendi iletişim kutusunu yapılandırmak yerine, yazı tipi seçimi için basit bir çözüm olarak Windows tabanlı uygulamanızın içinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2d8e-104">Use it within your Windows-based application as a simple solution for font selection in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="b2d8e-105">Varsayılan olarak, iletişim kutusu yazı tipi, yazı tipi stili ve boyut için liste kutularını gösterir; Üstü çizili ve altı çizili gibi efektler için onay kutuları; Betik için bir açılır liste; ve yazı tipinin nasıl görüneceğini gösteren bir örnek.</span><span class="sxs-lookup"><span data-stu-id="b2d8e-105">By default, the dialog box shows list boxes for Font, Font style, and Size; check boxes for effects like Strikeout and Underline; a drop-down list for Script; and a sample of how the font will appear.</span></span> <span data-ttu-id="b2d8e-106">(Komut dosyası, örneğin Ibranice veya Japonca gibi belirli bir yazı tipi için kullanılabilen farklı karakter betikleri anlamına gelir.) Yazı tipi iletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="b2d8e-106">(Script refers to different character scripts that are available for a given font, for example, Hebrew or Japanese.) To display the font dialog box, call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="b2d8e-107">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="b2d8e-107">Key Properties</span></span>  
 <span data-ttu-id="b2d8e-108">Bileşenin görünümünü yapılandıran bir dizi özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="b2d8e-108">The component has a number of properties that configure its appearance.</span></span> <span data-ttu-id="b2d8e-109">İletişim kutusu seçimlerini ayarlamaya yönelik özellikler <xref:System.Windows.Forms.FontDialog.Font%2A> ve <xref:System.Windows.Forms.FontDialog.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2d8e-109">The properties that set the dialog-box selections are <xref:System.Windows.Forms.FontDialog.Font%2A> and <xref:System.Windows.Forms.FontDialog.Color%2A>.</span></span> <span data-ttu-id="b2d8e-110"><xref:System.Windows.Forms.FontDialog.Font%2A> özelliği, yazı tipi, stil, boyut, komut dosyası ve etkileri belirler; Örneğin, `Arial, 10pt, style=Italic, Strikeout`.</span><span class="sxs-lookup"><span data-stu-id="b2d8e-110">The <xref:System.Windows.Forms.FontDialog.Font%2A> property sets the font, style, size, script, and effects; for example, `Arial, 10pt, style=Italic, Strikeout`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2d8e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2d8e-111">See also</span></span>

- <xref:System.Windows.Forms.FontDialog>
- [<span data-ttu-id="b2d8e-112">FontDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="b2d8e-112">FontDialog Component</span></span>](fontdialog-component-windows-forms.md)
