---
title: WPF Denetimlerini Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5e05ec7fc503565333a4d05662a4e40d8d1193af
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197466"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a><span data-ttu-id="fcaec-102">Windows Forms uygulamalarında WPF denetimlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="fcaec-102">Use WPF controls in Windows Forms apps</span></span>

<span data-ttu-id="fcaec-103">Windows Forms tabanlı uygulamalarda Windows Presentation Foundation (WPF) denetimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcaec-103">You can use Windows Presentation Foundation (WPF) controls in Windows Forms-based applications.</span></span> <span data-ttu-id="fcaec-104">Bunlar iki farklı görünüm teknolojisidir, ancak sorunsuz bir şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="fcaec-104">Although these are two different view technologies, they interoperate smoothly.</span></span>

<span data-ttu-id="fcaec-105">Visual Studio 'daki Windows Form Tasarımcısı, Windows Presentation Foundation denetimleri barındırmak için görsel tasarım ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcaec-105">The Windows Forms Designer in Visual Studio provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="fcaec-106">WPF denetimi, <xref:System.Windows.Forms.Integration.ElementHost>adında özel bir Windows Forms denetimi tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="fcaec-106">A WPF control is hosted by a special Windows Forms control that's named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="fcaec-107">Bu denetim WPF denetiminin formun düzenine katılmasını ve klavye ve fare iletilerini almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcaec-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="fcaec-108">Tasarım zamanında, <xref:System.Windows.Forms.Integration.ElementHost> denetimini tıpkı herhangi bir Windows Forms denetimine yaptığınız gibi düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcaec-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>

<span data-ttu-id="fcaec-109">WPF tabanlı uygulamalarda Windows Forms denetimlerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcaec-109">You can also use Windows Forms controls in WPF-based applications.</span></span> <span data-ttu-id="fcaec-110">Daha fazla bilgi için bkz. [Visual Studio 'DA xaml tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="fcaec-110">For more information, see [Design XAML in Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span></span>

## <a name="see-also"></a><span data-ttu-id="fcaec-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcaec-111">See also</span></span>

- [<span data-ttu-id="fcaec-112">WPF ve Windows Forms birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="fcaec-112">WPF and Windows Forms interoperation</span></span>](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)
