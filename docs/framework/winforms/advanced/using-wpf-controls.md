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
# <a name="use-wpf-controls-in-windows-forms-apps"></a>Windows Forms uygulamalarında WPF denetimlerini kullanma

Windows Forms tabanlı uygulamalarda Windows Presentation Foundation (WPF) denetimleri kullanabilirsiniz. Bunlar iki farklı görünüm teknolojisidir, ancak sorunsuz bir şekilde çalışır.

Visual Studio 'daki Windows Form Tasarımcısı, Windows Presentation Foundation denetimleri barındırmak için görsel tasarım ortamı sağlar. WPF denetimi, <xref:System.Windows.Forms.Integration.ElementHost>adında özel bir Windows Forms denetimi tarafından barındırılır. Bu denetim WPF denetiminin formun düzenine katılmasını ve klavye ve fare iletilerini almasını sağlar. Tasarım zamanında, <xref:System.Windows.Forms.Integration.ElementHost> denetimini tıpkı herhangi bir Windows Forms denetimine yaptığınız gibi düzenleyebilirsiniz.

WPF tabanlı uygulamalarda Windows Forms denetimlerini de kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'DA xaml tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

## <a name="see-also"></a>Ayrıca bkz.

- [WPF ve Windows Forms birlikte çalışma](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)
