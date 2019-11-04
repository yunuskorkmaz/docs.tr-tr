---
title: WPF Denetimlerini Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9883e9d31fc9e3e2ec3ca06b4fc830bcdc338ae
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460701"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a><span data-ttu-id="35faf-102">Windows Forms uygulamalarında WPF denetimlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="35faf-102">Use WPF controls in Windows Forms apps</span></span>

<span data-ttu-id="35faf-103">Windows Forms tabanlı uygulamalarda Windows Presentation Foundation (WPF) denetimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35faf-103">You can use Windows Presentation Foundation (WPF) controls in Windows Forms-based applications.</span></span> <span data-ttu-id="35faf-104">Bunlar iki farklı görünüm teknolojisidir, ancak sorunsuz bir şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="35faf-104">Although these are two different view technologies, they interoperate smoothly.</span></span>

<span data-ttu-id="35faf-105">Visual Studio 'daki Windows Form Tasarımcısı, Windows Presentation Foundation denetimleri barındırmak için görsel tasarım ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="35faf-105">The Windows Forms Designer in Visual Studio provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="35faf-106">WPF denetimi, <xref:System.Windows.Forms.Integration.ElementHost>adında özel bir Windows Forms denetimi tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="35faf-106">A WPF control is hosted by a special Windows Forms control that's named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="35faf-107">Bu denetim WPF denetiminin formun düzenine katılmasını ve klavye ve fare iletilerini almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="35faf-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="35faf-108">Tasarım zamanında, <xref:System.Windows.Forms.Integration.ElementHost> denetimini tıpkı herhangi bir Windows Forms denetimine yaptığınız gibi düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35faf-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>

<span data-ttu-id="35faf-109">WPF tabanlı uygulamalarda Windows Forms denetimlerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35faf-109">You can also use Windows Forms controls in WPF-based applications.</span></span> <span data-ttu-id="35faf-110">Daha fazla bilgi için bkz. [Visual Studio 'DA xaml tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="35faf-110">For more information, see [Design XAML in Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span></span>

## <a name="see-also"></a><span data-ttu-id="35faf-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35faf-111">See also</span></span>

- [<span data-ttu-id="35faf-112">WPF ve Windows Forms birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="35faf-112">WPF and Windows Forms interoperation</span></span>](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)
