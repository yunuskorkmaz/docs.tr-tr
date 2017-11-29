---
title: "FontDialog Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1e00fc074148ddd53885bafbb490a3e3868fc0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="fontdialog-component-overview-windows-forms"></a><span data-ttu-id="7457d-102">FontDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7457d-102">FontDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="7457d-103">Windows Forms <xref:System.Windows.Forms.FontDialog> bileşenidir standart Windows bir önceden yapılandırılmış iletişim kutusu **yazı tipi** sistemde yüklü yazı tiplerini kullanıma sunmak için kullanılan iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="7457d-103">The Windows Forms <xref:System.Windows.Forms.FontDialog> component is a pre-configured dialog box, which is the standard Windows **Font** dialog box used to expose the fonts that are currently installed on the system.</span></span> <span data-ttu-id="7457d-104">Basit bir çözüm olarak, Windows tabanlı uygulamanızda kendi iletişim kutusu yapılandırma yerine yazı tipi seçimi için kullanın.</span><span class="sxs-lookup"><span data-stu-id="7457d-104">Use it within your Windows-based application as a simple solution for font selection in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="7457d-105">Varsayılan olarak, liste kutuları iletişim kutusu, yazı tipini gösterir. yazı tipi stili ve boyutu; üstü çizili ve alt çizgi gibi etkileri onay kutularını; komut dosyası için aşağı açılan listesi; ve yazı tipi nasıl görüneceğini bir örnek.</span><span class="sxs-lookup"><span data-stu-id="7457d-105">By default, the dialog box shows list boxes for Font, Font style, and Size; check boxes for effects like Strikeout and Underline; a drop-down list for Script; and a sample of how the font will appear.</span></span> <span data-ttu-id="7457d-106">(Betik verilen yazı tipi için kullanılabilen farklı karakter betikleri Örneğin, İbranice veya Japonca ifade eder.) Yazı tipi iletişim kutusu görüntülemek için arama <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7457d-106">(Script refers to different character scripts that are available for a given font, for example, Hebrew or Japanese.) To display the font dialog box, call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="7457d-107">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="7457d-107">Key Properties</span></span>  
 <span data-ttu-id="7457d-108">Bileşen bir dizi görünümünü yapılandırma özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="7457d-108">The component has a number of properties that configure its appearance.</span></span> <span data-ttu-id="7457d-109">İletişim kutusu seçimleri ayarlamak Özellikler <xref:System.Windows.Forms.FontDialog.Font%2A> ve <xref:System.Windows.Forms.FontDialog.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="7457d-109">The properties that set the dialog-box selections are <xref:System.Windows.Forms.FontDialog.Font%2A> and <xref:System.Windows.Forms.FontDialog.Color%2A>.</span></span> <span data-ttu-id="7457d-110"><xref:System.Windows.Forms.FontDialog.Font%2A> Özelliği ayarlar yazı tipini, stili, boyutu, komut dosyası ve etkiler; Örneğin, `Arial, 10pt, style=Italic, Strikeout`.</span><span class="sxs-lookup"><span data-stu-id="7457d-110">The <xref:System.Windows.Forms.FontDialog.Font%2A> property sets the font, style, size, script, and effects; for example, `Arial, 10pt, style=Italic, Strikeout`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7457d-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7457d-111">See Also</span></span>  
 <xref:System.Windows.Forms.FontDialog>  
 [<span data-ttu-id="7457d-112">FontDialog bileşeni</span><span class="sxs-lookup"><span data-stu-id="7457d-112">FontDialog Component</span></span>](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
